```
mis_postprocessing(graph::AbstractGraph; ntrials::Int = 10)
```

[`mis_postprocessing`](@ref) のカリー化されたバージョンです。

# 例

ハーバード実験で使用された後処理を用いて `rydberg_density_sum` 損失を計算する: [arxiv:2202.09372](https://arxiv.org/abs/2202.09372)。

```julia
rydberg_density_sum(mis_postprocessing(graph), reg)
```
