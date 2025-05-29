```
struct MiniBatchContext{Tctx, T} <: AbstractContext
    context::Tctx
    loglike_scalar::T
end
```

`MiniBatchContext`は、モデルを実行する際に`log(prior) + s * log(likelihood of a batch)`の計算を可能にします。ここで`s`は`loglike_scalar`フィールドで、通常は`データポイントの数 / バッチサイズ`に等しいです。これは、バッチベースの確率的勾配降下アルゴリズムで、期待値において`log(prior) + log(all the data pointsのlikelihood)`を最適化するのに役立ちます。
