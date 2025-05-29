```
evolutionApproximate!(op_array, op0, tspan, Hamiltonian)
```

`op0`の近似時間発展を$U(t)$に基づいてインプレースで計算します。$t_0$と$t_\text{step}$のために計算されます。 [`evolutionOperator`](@ref)を参照してください。このメソッドは配列のベクトルを返します。
