```
extrapolate_fdm(
    m::FiniteDifferenceMethod,
    f,
    x::Real,
    initial_step::Real=10,
    power::Int=1,
    breaktol::Real=Inf,
    kw_args...
)
```

リチャードソン外挿を使用して有限差分法を外挿します。

`Richardson.extrapolate`のキーワード引数をさらに受け取ります。このメソッドは、`m`が対称の場合は自動的に`power = 2`を設定し、`power = 1`を設定します。さらに、`breaktol = Inf`がデフォルトです。

# 引数

  * `m::FiniteDifferenceMethod`: ステップサイズを推定するための有限差分法。
  * `f`: 導関数を評価する関数。
  * `x::Real`: 導関数を推定する点。
  * `initial_step::Real=10`: 初期ステップサイズ。

# 戻り値

  * `Tuple{<:AbstractFloat, <:AbstractFloat}`: 導関数の推定値と誤差。
