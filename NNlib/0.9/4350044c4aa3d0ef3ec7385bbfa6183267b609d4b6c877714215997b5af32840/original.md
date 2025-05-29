```
ctc_loss(ŷ, y)
```

Computes the connectionist temporal classification loss between `ŷ` and `y`. `ŷ` must be a classes-by-time matrices, i.e., each row represents a class and each column represents a time step. Additionally, the `logsoftmax` function will be applied to `ŷ`, so `ŷ` must be the raw activation values from the neural network and not, for example, the activations after being passed through a `softmax` activation function. `y` must be a 1D array of the labels associated with `ŷ`. The blank label is assumed to be the last label category in `ŷ`, so it is equivalent to `size(ŷ, 1)`. Used for sequence-to-sequence classification problems such as speech recognition and handwriting recognition where the exact time-alignment of the output (e.g., letters) is not needed to solve the problem. See [Graves et al. (2006)](https://www.cs.toronto.edu/~graves/icml_2006.pdf) or [Graves (2012)](https://www.cs.toronto.edu/~graves/preprint.pdf#chapter.7) for mathematical details.
