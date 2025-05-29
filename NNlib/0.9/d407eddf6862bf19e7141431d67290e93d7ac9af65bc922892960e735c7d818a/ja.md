```
logsumexp(x; dims = :)
```

数値的に安定した方法で `log.(sum(exp.(x); dims))` を計算します。`dims` キーワードなしではスカラーを返します。

関連情報として [`logsoftmax`](@ref) を参照してください。
