```
relative_entropy([base=2,] p::AbstractVector, q::AbstractVector)
```

2つの非負ベクトル `p` と `q` の間の相対エントロピー D(`p`||`q`) = Σᵢpᵢlog(pᵢ/qᵢ) を、基数 `base` の対数を使用して計算します。`p` のサポートは `q` のサポートに含まれている必要がありますが、効率のためにこれはチェックされません。

参考文献: [相対エントロピー](https://en.wikipedia.org/wiki/Relative_entropy)
