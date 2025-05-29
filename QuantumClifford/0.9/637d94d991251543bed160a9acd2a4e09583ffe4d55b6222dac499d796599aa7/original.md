Perform the Symplectic Gram-Schmidt procedure that gives a Clifford operator canonically related to a given Pauli operator.

The algorithm is detailed in [koenig2014efficiently](@cite).

```jldoctest
julia> symplecticGS(P"X", padded_n=3)
X₁ ⟼ + X__
X₂ ⟼ + _X_
X₃ ⟼ + __X
Z₁ ⟼ + Z__
Z₂ ⟼ + _Z_
Z₃ ⟼ + __Z

julia> symplecticGS(P"Z")
X₁ ⟼ + Z
Z₁ ⟼ + X
```

See also: [`enumerate_cliffords`](@ref), [`clifford_cardinality`](@ref).
