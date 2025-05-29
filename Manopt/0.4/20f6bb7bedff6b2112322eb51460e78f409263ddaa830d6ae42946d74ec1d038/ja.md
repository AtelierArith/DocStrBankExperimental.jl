```
StochasticGradient <: AbstractGradientGroupProcessor
```

デフォルトの勾配プロセッサで、（確率的）勾配またはそのサブセットを評価するだけです。

# コンストラクタ

```
StochasticGradient(M::AbstractManifold; p=rand(M), X=zero_vector(M, p))
```

接ベクトル型の `X` で確率的勾配プロセッサを初期化します。ここで、`M` と `p` は単なる補助変数です。
