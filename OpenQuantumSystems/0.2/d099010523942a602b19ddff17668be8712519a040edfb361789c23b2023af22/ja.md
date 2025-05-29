```
evolution_exact(rho0, tspan, Hamiltonian; diagonalize = false)
```

$$
U(t)
$$

に基づいて`rho0`の近似時間発展を計算します。これは$t_0$と$t_\text{step}$のために計算されます。`diagonalize`引数はハミルトニアンを$\lambda_i, S, S^{-1}$に分解し、固有値分解を使用して指数関数を計算します。[`evolutionOperator`](@ref)を参照してください。このメソッドはtspanと演算子のベクトルを返します。
