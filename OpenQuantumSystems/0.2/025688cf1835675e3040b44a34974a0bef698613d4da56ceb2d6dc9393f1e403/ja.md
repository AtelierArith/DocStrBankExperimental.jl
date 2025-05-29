```
evolution_exact(rho0, tspan, Hamiltonian; diagonalize = false)
```

`rho0`に基づいて$U(t)$に基づく正確な時間発展をインプレースで計算します。`diagonalize`引数はハミルトニアンを$\lambda_i, S, S^{-1}$に分解し、固有値分解を使用して指数関数を計算します。[`evolutionOperator`](@ref)を参照してください。このメソッドはtspanと演算子のベクトルを返します。
