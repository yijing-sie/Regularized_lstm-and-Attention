# Regularized_lstm-and-Attention


Intro to Deep Learning assignment:

## Regularized lstm


The first part of this assignment is to **predict the next word** and **generate text** for the `test` set from the pre-processed WikiText-2 Language Modeling Dataset by employing various techniques to **regularize** an LSTM model for better performance 

* The techniques are all from [Regularizing and Optimizing LSTM Language Models](https://arxiv.org/pdf/1708.02182.pdf)
* All the details for this part can be found in [regularized_lstm.ipynb](regularized_lstm.ipynb)
* [regularized_lstm.ipynb](regularized_lstm.ipynb) uses the class `LanguageModelTrainer` and the class `TestLanguageModel` to train on the `train` set, to print the **Negative Log Likelihood (NLL)** for the prediction task on the `train` and `dev` set, and then to predict the next words and generate texts for the `test` dataset
* **Prediction of the Next Word**: In class `TestLanguageModel`, the function `prediction` takes as input a batch of sequences and returns the raw scores for the next word for each sequence 
> The prediction scores for the `dev` and `test` set are stored in [predictions-39.npy](1660560996/predictions-39.npy) and [predictions-test-39.npy](1660560996/predictions-test-39.npy) respectively
* **Generation of a Sequence**: In class `TestLanguageModel`, the function `generation` takes as input a batch of sequences and generates a sequence for each provided sequence 
> The generated texts for the `dev` and `test` set are stored in [generated-39.txt](1660560996/generated-39.txt) and [generated-39-test.txt](1660560996/generated-39-test.txt) respectively
* This model achieves a **4.75** mean NLL score for the prediction of the next word and a **1.88** mean NLL for the generation of a sequence on the `test` set
### The model's loss curve
<p>
  <img src="/1660560996/loss.png" width="400" title="loss curve"/>
</p>

## Attention plot
For this part, the goal is to implement a character-based **Seq2Seq** model with **attention** & **teacher-forcing** mechanisms to retrieve a clear diagonal attention plot for validation data.

* The baseline model is a simplified version of the [Listen, Attend and Spell paper](https://arxiv.org/pdf/1508.01211.pdf?undefined) without the pyramid BLSTM layers in the encoder.
* More specifically, the model uses **dot-product attention** with one layer of Bi-LSTM in the encoder and two LSTMCells in the decoder.
* **Training features**: Random sequences of embedded characters, each of variable length and 40 frequency bands
* **Training labels**: Transcripts corresponding to the training features
> A screenshot  of the first training feature (left) and its corresponding training label (right)
<p float="left">
 <img src="train_X_sample.png" width="500" />
 <img src="train_y_sample.png" width="300" />
</p>

* [attention_plots](attention_plots) stores the **attention** plots for the first 10 validation samples, which are also stored as numpy array in [attention.npy](attention.npy). 
### The attention plot for the first validation data generated from the model:
<p>
  <img src="/attention_plots/attention_0.png" width="400" title="attention_0"/>
</p>

* The model details can be found in [attention.ipynb](attention.ipynb)

