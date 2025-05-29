```
categorical(probs::AbstractArray{U, 1}) where {U <: Real}
```

確率のベクトル `probs` が与えられたとき、`sum(probs) = 1` である。集合 {1, 2, .., `length(probs)`} から、確率 `probs[i]` で整数 `i` をサンプリングする。
