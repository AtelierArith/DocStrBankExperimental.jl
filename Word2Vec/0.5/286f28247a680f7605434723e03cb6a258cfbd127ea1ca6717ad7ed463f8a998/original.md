```
 word2phrase(train, output; min_count=5, threshold=100, debug=2)

Parameters for training:
train <file>
      Use text data from <file> to train the model 
output <file>
          Use <file> to save the resulting word vectors / 
          word clusters / phrases
min_count <Int>
          This will discard words that appear less than <int> times; 
          default is 5
threshold <AbstractFloat>
  	      The <AbstractFloat> value represents threshold for 
          forming the phrases (higher means less phrases); default 100
debug <Int>
      Set the debug mode (default = 2 = more info during training)
```
