```
ShiftingField <: Hamiltonian
ShiftingField(magnitude::Union{Field, TimeSeries}) -> ShiftingField
```

[`Hamiltonian`](@ref)内のシフトフィールドを表し、[`AnalogHamiltonianSimulation`](@ref)におけるライデbergレベルのエネルギーを変化させます。

$$
H_{sf}(t) = - \Delta(t) \sum_k h_k \left| r_k \right\rangle\left\langle r_k \right|
$$

ここで、$\left| r_k \right\rangle$は原子$k$のライデberg状態であり、$h_k$は0から1の間の無次元実数のローカルパターンです。

引数`magnitude`は、時間が秒単位で、値がラジアン/秒単位のグローバルマグニチュード時間系列$\Delta(t)$を表します。
