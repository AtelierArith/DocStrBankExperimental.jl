```
evolutionExact(ket0, tspan, Hamiltonian; diagonalize = true, approximate = false)
```

`ket0` 状態の正確な時間発展を計算します。詳細は [`evolutionOperatorIterator`](@ref) を参照してください。`diagonalize` 引数はハミルトニアンを $\lambda_i, S, S^{-1}$ に分解し、固有値分解を使用して指数関数を計算します。`approximate` オプションは、tspan が等間隔の点で構成されていることを前提としているため、$U(t)$ は $t_0$ と $t_\text{step}$ のために計算される必要があります。
