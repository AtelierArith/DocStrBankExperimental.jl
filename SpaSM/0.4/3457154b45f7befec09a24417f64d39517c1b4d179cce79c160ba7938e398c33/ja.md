```
solve(fact::LU{F}, b::Vector{ZZp{F}}, x::Union{Vector{ZZp{F}},Nothing} = nothing)
```

`x`*`A` == `b` を解きます。ここで `A` はすでにエシュロン化されている `fact` です。解 `x` を返すか、解がない場合は `nothing` を返します。
