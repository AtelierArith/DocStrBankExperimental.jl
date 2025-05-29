The size of the Clifford group `𝒞` over a given number of qubits, possibly modulo the phases.

For n qubits, not accounting for phases is `2ⁿⁿΠⱼ₌₁ⁿ(4ʲ-1)`. There are `4ⁿ` different phase configurations.

```jldoctest
julia> clifford_cardinality(7)
457620995529680351512370381586432000
```

When not accounting for phases (`phases = false`) the result is the same as the size of the Symplectic group `Sp(2n) ≡ 𝒞ₙ/𝒫ₙ`, where `𝒫ₙ` is the Pauli group over `n` qubits.

```jldoctest
julia> clifford_cardinality(7, phases=false)
27930968965434591767112450048000
```

See also: [`enumerate_cliffords`](@ref).
