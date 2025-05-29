Generate a symbolic single-qubit gate given its index. Optionally, set non-trivial phases.

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

See also: [`enumerate_cliffords`](@ref).
