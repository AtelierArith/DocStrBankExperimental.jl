```
create(N::Int)
```

Bosonic creation operator with Hilbert space cutoff `N`.

This operator acts on a fock state as $\hat{a}^\dagger \ket{n} = \sqrt{n+1} \ket{n+1}$.

# Examples

```jldoctest
julia> a_d = create(20)

Quantum Object:   type=Operator()   dims=[20]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} with 19 stored entries:
⎡⠢⡀⠀⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠀⠈⠢⡀⠀⠀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠈⠢⡀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠈⠢⡀⠀⠀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠈⠢⡀⎦

julia> fock(20, 4)' * a_d * fock(20, 3)
2.0 + 0.0im
```
