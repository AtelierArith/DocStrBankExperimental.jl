```
evolutionSuperOperatorIterator(Hamiltonian, tspan; 
	diagonalize = true, approximate = false)
```

再開可能な関数で、tspanの時刻tでの演算子をOperator型として返します。[`evolutionSuperOperator`](@ref)を参照してください。`diagonalize`引数はハミルトニアンを$\lambda_i, S, S^{-1}$に分解し、固有値分解を使用して指数関数を計算します。`approximate`オプションは、tspanが等間隔の点で構成されていることを前提としているため、$U(t)$は$t_0$と$t_\text{step}$のために計算される必要があります。
