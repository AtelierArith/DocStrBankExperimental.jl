```
(::Integrator)(s, N; grad=true)
```

呼び出し可能な [`Integrator`](@ref) メソッド。N ステップの積分を行います。

# 引数

  * `s::State{T}` : シミュレーションの現在の状態。
  * `N::Int64` : ステップ数。

### オプション

  * `grad::Bool` : 勾配を計算するかどうかを選択します。 (デフォルト = true)
