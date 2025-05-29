`orbits(a::Perm,d::AbstractVector{<:Integer};trivial=true)`

は、ドメイン `d` に対する `a` のオービットを返します。これは `a` のオービットの和集合であるべきです。`trivial=false` の場合、長さ `1` のオービットは返しません。

# 例

```julia-repl
julia> orbits(Perm(1,2)*Perm(4,5),1:5)
3-element Vector{Vector{Int64}}:
 [1, 2]
 [3]
 [4, 5]
```
