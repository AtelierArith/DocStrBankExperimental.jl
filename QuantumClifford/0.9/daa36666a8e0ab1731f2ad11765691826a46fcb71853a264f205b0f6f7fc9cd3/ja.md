シンボリックな単一量子ビットゲートをそのインデックスに基づいて生成します。オプションで、非自明な位相を設定します。

```jldoctest
julia> enumerate_single_qubit_gates(6)
sPhase on qubit 1
X₁ ⟼ + Y
Z₁ ⟼ + Z

julia> enumerate_single_qubit_gates(6, qubit=2, phases=(true, true))
SingleQubitOperator on qubit 2
X₁ ⟼ - Y
Z₁ ⟼ - Z
```

参照: [`enumerate_cliffords`](@ref).
