```
BayesModel(prior, logintegrand) <: AbstractBQModel
```

`AbstractMCMC.AbstractModel`から継承されたモデル。`prior`は`Distributions.jl`の多変量分布である必要があります。現時点では`prior`は`MvNormal`でなければなりませんが、これは後のバージョンで改善される予定です。`logintegrand`は積分する関数の対数である必要があります。
