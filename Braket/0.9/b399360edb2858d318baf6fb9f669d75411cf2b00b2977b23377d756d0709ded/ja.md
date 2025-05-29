```
DrivingField <: Hamiltonian
DrivingField(amplitude::Union{Field, TimeSeries}, phase::Union{Field, TimeSeries}, detuning::Union{Field, TimeSeries}) -> DrivingField
```

[`Hamiltonian`](@ref)内の駆動場を表し、[`AnalogHamiltonianSimulation`](@ref)において原子を基底状態からリュードベリ状態にコヒーレントに移行させます。

$$
H_{df}(t) = \frac{1}{2} \Omega(t)\exp(i \phi(t)) \sum_k \left( | g_k \rangle\langle r_k | + h.c.\right) - \Delta(t) \sum_k| r_k \rangle\langle r_k |
$$

ここで、$\left| g_k \right\rangle$は原子$k$の基底状態であり、$\left| r_k \right\rangle$は原子$k$のリュードベリ状態です。

# 引数

  * `amplitude`は全体の振幅$\Omega(t)$を表します。時間は秒単位で、値はラジアン/秒です。
  * `phase`は全体の位相$\phi(t)$を表します。時間は秒単位で、値はラジアン/秒です。
  * `detuning`は全体のデチューニング$\Delta(t)$を表します。時間は秒単位で、値はラジアン/秒です。
