```
binary_relative_entropy([base=2,] p::Real, q::Real)
```

Computes the binary relative entropy D(`p`||`q`) = p log(p/q) + (1-p) log((1-p)/(1-q)) between two probabilities `p` and `q` using a base `base` logarithm.

Reference: [Relative entropy](https://en.wikipedia.org/wiki/Relative_entropy)
