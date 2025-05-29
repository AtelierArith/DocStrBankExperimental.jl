```
glu(x, dim = 1)
```

The gated linear unit from the ["Language Modeling with Gated Convolutional Networks"](https://arxiv.org/abs/1612.08083) paper.

Calculates `a .* sigmoid(b)`, where `x` is split in half along given dimension `dim` to form `a` and `b`.
