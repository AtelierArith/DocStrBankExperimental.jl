```
ProportionalHazard(y)::RiskMeasure
ProportionalHazard(y)(risk)::T (where T is the type of values sampled in risk)
```

Proportional Hazard歪曲リスク測定は、$x^(1/y)$として定義されます。ここで、xはリスク分布の累積分布関数（CDF）であり、yは正のパラメータです。riskは単変量分布または結果の配列である可能性があります。ProportionalHazard(y)はファンクタを返し、その後リスク分布に対して呼び出すことができます。

## 例

```julia-repl
julia> ProportionalHazard(2)(rand(1000))
0.6659603556774121

julia> rm = ProportionalHazard(2)
ProportionalHazard{Int64}(2)

julia> rm(rand(1000))
0.6710587338367799
```
