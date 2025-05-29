```
kron(A::AbstractQuantumObject, B::AbstractQuantumObject, ...)
tensor(A::AbstractQuantumObject, B::AbstractQuantumObject, ...)
⊗(A::AbstractQuantumObject, B::AbstractQuantumObject, ...)
A ⊗ B
```

[クロネッカー積](https://en.wikipedia.org/wiki/Kronecker_product) $\hat{A} \otimes \hat{B} \otimes \cdots$ を返します。

!!! note
    `tensor` と `⊗`（`⊗` は REPL で `\otimes` をタブ補完することで入力できます）は `kron` の同義語です。


# 例

```jldoctest
julia> a = destroy(20)

量子オブジェクト:   type=Operator()   dims=[20]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} で 19 の格納エントリを持つ:
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
