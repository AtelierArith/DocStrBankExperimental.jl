`torus_order(W::ComplexReflectionGroup,i,q=Pol())`

は、`W`の`i`-番目の共役類のトーリックオーダーを`q`の多項式として返します。これは、そのクラスの要素の特性多項式であり、`W`の反射表現におけるものです。これは、トリビアル部分群と`i`-番目の共役類の代表によって決定される`W`の反射サブコセット`torus(W,i)`の一般的なオーダーと同じです。

```julia-repr
julia> W=complex_reflection_group(4)

julia> torus_order.(Ref(W),1:nconjugacy_classes(W),Pol(:q))
7-element Vector{Pol{Cyc{Int64}}}:
 q²-2q+1
 q²+2q+1
 q²+1
 q²-ζ₃q+ζ₃²
 q²+ζ₃q+ζ₃²
 q²+ζ₃²q+ζ₃
 q²-ζ₃²q+ζ₃
```
