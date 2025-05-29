```
@Tensor [a b; c d]
@Tensor [[a, b];[c, d]]
@Tensor [i+j for i in 1:2, j in 1:2]
@Tensor ones(2, 2, 2)
```

任意の次元を持つ `Tensor` を構築するための便利なマクロです。
