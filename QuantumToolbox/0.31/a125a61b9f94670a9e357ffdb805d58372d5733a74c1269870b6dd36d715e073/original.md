```
bell_state(x::Union{Int}, z::Union{Int})
```

Return the [Bell state](https://en.wikipedia.org/wiki/Bell_state) depending on the arguments `(x, z)`:

  * `(0, 0)`: $| \Phi^+ \rangle = ( |00\rangle + |11\rangle ) / \sqrt{2}$
  * `(0, 1)`: $| \Phi^- \rangle = ( |00\rangle - |11\rangle ) / \sqrt{2}$
  * `(1, 0)`: $| \Psi^+ \rangle = ( |01\rangle + |10\rangle ) / \sqrt{2}$
  * `(1, 1)`: $| \Psi^- \rangle = ( |01\rangle - |10\rangle ) / \sqrt{2}$

Here, `x = 1` (`z = 1`) means applying Pauli-$X$ ( Pauli-$Z$) unitary transformation on $| \Phi^+ \rangle$.

# Example

```jldoctest
julia> bell_state(0, 0)

Quantum Object:   type=Ket()   dims=[2, 2]   size=(4,)
4-element Vector{ComplexF64}:
 0.7071067811865475 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
 0.7071067811865475 + 0.0im

julia> bell_state(Val(1), Val(0))

Quantum Object:   type=Ket()   dims=[2, 2]   size=(4,)
4-element Vector{ComplexF64}:
                0.0 + 0.0im
 0.7071067811865475 + 0.0im
 0.7071067811865475 + 0.0im
                0.0 + 0.0im
```

!!! warning "Beware of type-stability!"
    If you want to keep type stability, it is recommended to use `bell_state(Val(x), Val(z))` instead of `bell_state(x, z)`. See [this link](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type) and the [related Section](@ref doc:Type-Stability) for more details.

