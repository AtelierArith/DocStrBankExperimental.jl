```
isconcretetype(T)
```

型 `T` が具体的な型であるかどうかを判断します。具体的な型とは、直接的なインスタンス（`typeof(x) === T` となる値 `x`）を持つことができる型を意味します。

関連情報: [`isbits`](@ref), [`isabstracttype`](@ref), [`issingletontype`](@ref).

# 例

```jldoctest
julia> isconcretetype(Complex)
false

julia> isconcretetype(Complex{Float32})
true

julia> isconcretetype(Vector{Complex})
true

julia> isconcretetype(Vector{Complex{Float32}})
true

julia> isconcretetype(Union{})
false

julia> isconcretetype(Union{Int,String})
false
```
