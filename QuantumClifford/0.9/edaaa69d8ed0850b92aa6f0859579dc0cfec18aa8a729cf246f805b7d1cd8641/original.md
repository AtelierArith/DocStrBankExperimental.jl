A "symbolic" general single-qubit operator which permits faster multiplication than an operator expressed as an explicit tableau.

```jldoctest
julia> op = SingleQubitOperator(2, true, true, true, false, true, true) # Tableau components and phases
SingleQubitOperator on qubit 2
X₁ ⟼ - Y
Z₁ ⟼ - X

julia> typeof(op)
SingleQubitOperator

julia> t_op = CliffordOperator(op, 3) # Transforming it back into an explicit tableau representation (specifying the size)
X₁ ⟼ + X__
X₂ ⟼ - _Y_
X₃ ⟼ + __X
Z₁ ⟼ + Z__
Z₂ ⟼ - _X_
Z₃ ⟼ + __Z

julia> typeof(t_op)
CliffordOperator{QuantumClifford.Tableau{Vector{UInt8}, Matrix{UInt64}}, PauliOperator{Array{UInt8, 0}, Vector{UInt64}}}

julia> CliffordOperator(op, 1, compact=true) # You can also extract just the non-trivial part of the tableau
X₁ ⟼ - Y
Z₁ ⟼ - X
```

See also: [`sHadamard`](@ref), [`sPhase`](@ref), [`sId1`](@ref), [`sX`](@ref), [`sY`](@ref), [`sZ`](@ref), [`CliffordOperator`](@ref)

Or simply consult `subtypes(QuantumClifford.AbstractSingleQubitOperator)` and `subtypes(QuantumClifford.AbstractTwoQubitOperator)` for a full list. You can think of the `s` prefix as "symbolic" or "sparse".
