```
     word2clusters(train, output, classes; size=100, window=5, sample=1e-3, hs=0,  negative=5, threads=1, iter=5, min_count=5, alpha=0.025, debug=2, binary=1, cbow=1, save_vocal=Nothing(), read_vocab=Nothing(), verbose=false)
```

```
Parameters for training:
    train <file>
        Use text data from <file> to train the model
    output <file>
        Use <file> to save the resulting word vectors / word clusters
    size <Int>
        Set size of word vectors; default is 100
    window <Int>
        Set max skip length between words; default is 5
    sample <AbstractFloat>
        Set threshold for occurrence of words. Those that appear with
        higher frequency in the training data will be randomly
        down-sampled; default is 0 (off), useful value is 1e-5
    hs <Int>
        Use Hierarchical Softmax; default is 1 (0 = not used)
    negative <Int>
        Number of negative examples; default is 0, common values are 5 - 10
        (0 = not used)
    threads <Int>
        Use <Int> threads (default 1)
    iter <Int>
        Run more training iterations (default 5)
    min_count <Int>
        This will discard words that appear less than <Int> times
        (default 5)
    alpha <AbstractFloat>
        Set the starting learning rate; default is 0.025
    classes <Int>
        Number of word classes; if 0, output word classes rather than
        word vectors (default 0)
    debug <Int>
        Set the debug mode (default = 2 = more info during training)
    binary <Int>
        Save the resulting vectors in binary moded; default is 0 (off)
    cbow <Int>
        Use the continuous back of words model; default is 1 (0 for skip-gram
        model)
    save_vocab <file>
        The vocabulary will be saved to <file>
    read_vocab <file>
        The vocabulary will be read from <file>, not constructed from the
        training data
    verbose <Bool>
        Print output from training
```
