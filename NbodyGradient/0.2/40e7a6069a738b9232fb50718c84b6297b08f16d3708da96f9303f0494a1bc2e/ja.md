```
(::Integrator)(s; grad=true)
```

呼び出し可能な [`Integrator`](@ref) メソッド。コンストラクタで指定された `s.t` から `tmax` まで統合します。

# 引数

  * `s::State{T}` : シミュレーションの現在の状態。

### オプション

  * `grad::Bool` : 勾配を計算するかどうかを選択します。 (デフォルト = true)
