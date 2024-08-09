# Text Emotion Recognition

## Dataset
The ISEAR dataset originally encompasses a wide range of emotional states. However, for our specific task, we focused on four primary emotions: Anger, Disgust, Joy, and Sadness. The dataset contains textual samples annotated with these emotions, providing a rich source for emotion recognition model training and evaluation.

* Dataset Link: [ISEAR Dataset](https://www.kaggle.com/datasets/faisalsanto007/isear-dataset?resource=download)
* Dataset Statistics:
  * Original Samples: 7,665
  * Original Labels: Joy, Anger, Sadness, Disgust, Guilt, Fear, Shame
  * Unique Values: 6,921
  * Processed Samples (After Filtering): 4,381
      * Fear: 1,095
      * Anger: 1,096
      * Joy: 1,094
      * Sadness: 1,096

## Model Architectures

### BERT-based Dual Channel Pipeline
The embedding module, dual-channel, and emotion classification are the three primary modules that make up the system. At its core lies the BERT embedding module where input sentences are tokenized and enhanced with specialized tokens before undergoing transformation. This model, equipped with 768 hidden units, 12 attention heads, and 12 transformer encoder blocks, converts each word into a multidimensional embedding vector, capturing nuanced linguistic features such as word position, context, and semantics. Following the embedding module, the system employs a dual-channel module, comprising both LSTM-CNN and CNN-LSTM channels. In the CNN-LSTM channel, textual features are extracted through convolutional operations before being forwarded to a Bidirectional LSTM (Bi-LSTM) layer, where sequential information is captured. Conversely, in the LSTM-CNN channel, the BERT embeddings are first processed through a convolutional layer to extract features before further refinement by a CNN. These channels are combined and passed through a series of dense layers for final classification.

![model_architecture](https://github.com/user-attachments/assets/631bb89b-7e34-4f62-a0d9-fab075eeccc3)

### RoBERTa-based Trichannel Pipeline
This approach leverages the RoBERTa (A Robustly Optimized BERT Pretraining Approach) model. The architecture consists of three channels:

1. Channel 1: A CNN layer for local feature extraction.
2. Channel 2: A BiLSTM layer with an attention mechanism for sequential context understanding.
3. Channel 3: A Transformer Encoder layer for contextual word representations.
   
These channels are combined and passed through a dense layer for final classification.

## Results

### BERT-based Dual Channel Pipeline
* Validation Accuracy: 84.28%
* F1-Score: 0.8442
* Precision: 0.8594
* Recall: 0.8428
* Confusion Matrix:
  
![image](https://github.com/user-attachments/assets/d09328d3-0550-4116-88ad-d573ee72672d)

### RoBERTa-based Trichannel Pipeline
* Validation Accuracy: 87.02%
* F1-Score: 0.8693
* Precision: 0.8726
* Recall: 0.8702
* Confusion Matrix:
  
  ![image](https://github.com/user-attachments/assets/2d01dbea-8ea0-4b76-8dcd-7d2c748716cf)
