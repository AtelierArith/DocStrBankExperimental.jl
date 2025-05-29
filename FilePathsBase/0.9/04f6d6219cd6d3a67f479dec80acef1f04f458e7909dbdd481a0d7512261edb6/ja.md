```
parents{T<:AbstractPath}(fp::T) -> Array{T}
```

パスのすべての親を返します。親が存在しない場合は、パスが絶対であるかどうかに応じて、"/" または "." が返されます。

# 例

```jldoctest
julia> parents(p"~/.julia/v0.6/REQUIRE")
3-element Array{PosixPath,1}:
 p"~"
 p"~/.julia"
 p"~/.julia/v0.6"

julia> parents(p"/etc")
1-element Array{PosixPath,1}:
 p"/"

julia> parents(p"etc")
1-element Array{PosixPath,1}:
 p"."

julia> parents(p".")
1-element Array{PosixPath,1}:
 p"."
```
