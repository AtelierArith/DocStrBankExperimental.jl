```
MajoranaSum{T}
MajoranaSum(terms::Vector{MajoranaTerm{T}})
MajoranaSum(terms::Dict{Vector{Int}, T})
MajoranaSum(op::AbstractBlock)
```

[`FLOYao.MajoranaTerm`](@ref)の和であり、[`expect`](@ref)および`expect'`において`op::Yao.AbstractBlock`のより高性能な置き換えとして使用されます。

(Pauliゲートのスケーリングされた) テンソル積の和である`Yao.AbstractBlock`は、直接`MajoranaSum`に変換できます：

```jldoctest; setup=:(using FLOYao, Yao)
julia> yaoham = (put(4, 1=>Z) + 2kron(4, 1=>X, 2=>Z, 3=>Z, 4=>X) + 3.5put(4, 2=>Z)
                 + 0.5kron(4, 1=>Z, 2=>Z) - kron(4, 2 => X, 4 => Y));

julia> MajoranaSum(yaoham)
5-element MajoranaSum{ComplexF64}:
  [4, 5, 6, 8] : -1.0 - 0.0im
  [2, 7] : 0.0 + 2.0im
  [1, 2, 3, 4] : -0.5 - 0.0im
  [1, 2] : 0.0 - 1.0im
  [3, 4] : 0.0 - 3.5im
```
