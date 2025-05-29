```
closestintersection(a::Union{EmptyInterval{T},Interval{T},DisjointUnion{T}}, ignorenull::Bool = true) -> Union{Nothing,Intersection{T,3}}
```

[`Interval`](@ref) または [`DisjointUnion`](@ref) から最も近い [`Intersection`](@ref) を返します。`ignorenull` が true の場合、null インターフェースとの交差は無視されます。有効な交差がない場合は `nothing` を返します。
