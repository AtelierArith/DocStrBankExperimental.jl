```
destroy(N::Int)
```

ヒルベルト空間のカットオフ `N` を持つボソニック消滅演算子です。

この演算子はフォック状態に対して $\hat{a} \ket{n} = \sqrt{n} \ket{n-1}$ のように作用します。

# 例

```jldoctest
julia> a = destroy(20)

Quantum Object:   type=Operator()   dims=[20]   size=(20, 20)   ishermitian=false
20×20 SparseMatrixCSC{ComplexF64, Int64} with 19 stored entries:
⎡⠈⠢⡀⠀⠀⠀⠀⠀⠀⠀⎤
⎢⠀⠀⠈⠢⡀⠀⠀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠈⠢⡀⠀⠀⠀⎥
⎢⠀⠀⠀⠀⠀⠀⠈⠢⡀⠀⎥
⎣⠀⠀⠀⠀⠀⠀⠀⠀⠈⠢⎦

julia> fock(20, 3)' * a * fock(20, 4)
2.0 + 0.0im
```
