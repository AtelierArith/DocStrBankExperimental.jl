```
parent{T<:AbstractPath}(fp::T) -> T
```

指定されたパスの親を返します。親が存在しない場合は、パスが絶対であるかどうかに応じて、"/" または "." が返されます。

# 例

```jldoctest
julia> parent(p"~/.julia/v0.6/REQUIRE")
p"~/.julia/v0.6"

julia> parent(p"/etc")
p"/"

julia> parent(p"etc")
p"."

julia> parent(p".")
p"."
```
