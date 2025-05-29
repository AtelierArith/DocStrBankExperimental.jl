```
kron(A::AbstractQuantumObject, B::AbstractQuantumObject, ...)
tensor(A::AbstractQuantumObject, B::AbstractQuantumObject, ...)
⊗(A::AbstractQuantumObject, B::AbstractQuantumObject, ...)
A ⊗ B
```

Returns the [Kronecker product](https://en.wikipedia.org/wiki/Kronecker_product) $\hat{A} \otimes \hat{B} \otimes \cdots$.

!!! note
    `tensor` and `⊗` (where `⊗` can be typed by tab-completing `\otimes` in the REPL) are synonyms of `kron`.


# Examples

```jldoctest
julia> a = destroy(20)

Quantum Object:   type=Operator()   dims=[20]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} with 19 stored entries:
⎡⠈⠢⡀⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠀⠀⠈⠢⡀⠀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠈⠢⡀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠀⠈⠢⡀⠀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠀⠈⠢⎦

julia> O = kron(a, a);

julia> size(a), size(O)
((20, 20), (400, 400))

julia> a.dims, O.dims
([20], [20, 20])
```
