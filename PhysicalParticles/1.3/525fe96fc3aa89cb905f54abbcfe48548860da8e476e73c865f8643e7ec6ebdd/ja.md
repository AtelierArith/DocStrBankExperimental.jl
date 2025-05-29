```
assign_particles(particles::Array{P,N} where P<:AbstractParticle, symbol::Symbol, data::Array) where N
```

`particles`のシンボルを`data`の要素と1つずつ割り当てます。`particles`と`data`は同じ長さでなければなりません。

## 例

```jl
julia> assign_particles([Ball(uSI) for i=1:3], :Pos, rand(PVector{Float64}, 3) * u"m")
```
