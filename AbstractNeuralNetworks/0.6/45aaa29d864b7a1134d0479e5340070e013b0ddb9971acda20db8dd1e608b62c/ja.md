```
initialparameters

モデル、すなわちレイヤーまたはチェーンの初期パラメータを返します。
```

```
initialparameters(backend::NeuralNetworkBackend, ::Type{T}, model::Model; init::Initializer = default_initializer(), rng::AbstractRNG = Random.default_rng())
initialparameters(::Type{T}, model::Model; init::Initializer = default_initializer(), rng::AbstractRNG = Random.default_rng())
```

`init!`関数は次のシグネチャを持たなければなりません：

```
init!(rng::AbstractRNG, x::AbstractArray)
```

`default_initializer()`は`randn!`を返します。
