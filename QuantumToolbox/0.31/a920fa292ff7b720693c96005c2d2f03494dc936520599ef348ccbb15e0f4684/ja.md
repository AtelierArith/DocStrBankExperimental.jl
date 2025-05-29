```
create(N::Int)
```

ヒルベルト空間のカットオフ `N` を持つボソニック生成演算子。

この演算子はフォック状態に対して $\hat{a}^\dagger \ket{n} = \sqrt{n+1} \ket{n+1}$ のように作用します。

# 例

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
