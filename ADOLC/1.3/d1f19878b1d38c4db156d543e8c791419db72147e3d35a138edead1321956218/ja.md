```
partial_to_adolc_format!(res::Vector{Cint}, partial::Vector{I_1}, degree::I_2) where {I_1<:Integer, I_2<:Integer}
partial_to_adolc_format!(res::Vector{Cint}, partial::Vector{Cint}, degree::I) where I <: Integer
```

[`partial_to_adolc_format`](@ref) のバリアントで、結果を `res` に書き込みます。

# 例:

```jldoctest
partial = [1, 3, 2, 0]
degree = sum(partial)
res = zeros(Int32, degree)
partial_to_adolc_format!(res, partial, degree)

# 出力

6-element Vector{Int32}:
 3
 3
 2
 2
 2
 1
```
