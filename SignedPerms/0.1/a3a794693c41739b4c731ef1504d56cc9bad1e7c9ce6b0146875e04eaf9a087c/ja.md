`SPerm{T}(m::AbstractMatrix)` もし `m` が符号付き置換行列であれば、対応する符号付き置換を型 `T` で返します。省略した場合、`T` は `Int16` として扱われます。

```julia-repl
julia> m=[0 -1 0;-1 0 0;0 0 -1]
3×3 Matrix{Int64}:
  0  -1   0
 -1   0   0
  0   0  -1

julia> SPerm(m)
(1,-2)(3,-3)
```
