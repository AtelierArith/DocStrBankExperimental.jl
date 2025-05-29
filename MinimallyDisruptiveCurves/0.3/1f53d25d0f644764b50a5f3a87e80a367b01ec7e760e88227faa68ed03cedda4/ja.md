```
HamiltonianResidual(timepoints::AbstractRange)
HamiltonianResidual(timepoints::Vector{<:AbstractFloat})
```

@info REPL出力を、timepoints::Vector{<:AbstractFloat}におけるハミルトニアンのu導関数dHduの数値で表示します。

例 c = HamiltonianResidual(0.1:0.1:2.1)

cはその後、Verbose()の引数として使用でき、次にevolveにキーワード引数として渡されます。
