```
binary_relative_entropy([base=2,] p::Real, q::Real)
```

2つの確率 `p` と `q` の間のバイナリ相対エントロピー D(`p`||`q`) = p log(p/q) + (1-p) log((1-p)/(1-q)) を、基数 `base` の対数を使用して計算します。

参考文献: [Relative entropy](https://en.wikipedia.org/wiki/Relative_entropy)
