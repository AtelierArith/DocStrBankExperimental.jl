```
typeof(x)
```

`x`の具体的な型を取得します。

関連情報として[`eltype`](@ref)も参照してください。

# 例

```jldoctest
julia> a = 1//2;

julia> typeof(a)
Rational{Int64}

julia> M = [1 2; 3.5 4];

julia> typeof(M)
Matrix{Float64} (alias for Array{Float64, 2})
```
