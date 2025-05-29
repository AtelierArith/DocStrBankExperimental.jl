```
simulate(series::Vector{T}, gas::ScoreDrivenModel{D, T}, H::Int, S::Int, kwargs...) where {D, T}
```

時間系列の将来のシナリオを生成するために、GAS再帰を`H`回更新し、分布のサンプルを取得して`S`シナリオを生成します。

デフォルトでは、このメソッドはスコア駆動再帰を実行するために`stationary_initial_params`メソッドを使用します。異なる`initial_params`のセットでモデルを推定した場合は、推定の一貫性を保つためにここでそれらを使用してください。
