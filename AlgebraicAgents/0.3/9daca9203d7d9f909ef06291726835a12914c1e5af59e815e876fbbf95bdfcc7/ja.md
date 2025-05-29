```
simulate(agent::AbstractAlgebraicAgent, max_t=Inf)::AbstractAlgebraicAgent
```

初期化された問題を解決します。すべてのエージェントが `true`（シミュレーションの地平線に到達）または `nothing`（委任された進化）を返すまで、またはシミュレーションの地平線が `max_t` に達するまでループを実行します。フロントランニングを回避します。

# 例

```julia
sol = simulate(model)
```
