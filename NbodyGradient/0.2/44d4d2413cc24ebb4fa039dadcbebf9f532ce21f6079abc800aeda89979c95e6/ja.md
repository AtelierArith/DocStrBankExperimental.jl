```
(::Integrator)(s, time; grad=true)
```

呼び出し可能な [`Integrator`](@ref) メソッド。特定の時間まで積分します。

# 引数

  * `s::State{T}` : シミュレーションの現在の状態。
  * `time::T` : 積分する時間。

### オプション

  * `grad::Bool` : 勾配を計算するかどうかを選択します。 (デフォルト = true)
