```
evolutionApproximate!(ket_array, ket0, tspan, Hamiltonian)
```

`ket0`の近似時間発展を、$U(t)$に基づいてインプレースで計算します。$t_0$と$t_\text{step}$のために計算されます。[`evolutionOperator`](@ref)を参照してください。引数`ket_array`は配列のベクトルです。
