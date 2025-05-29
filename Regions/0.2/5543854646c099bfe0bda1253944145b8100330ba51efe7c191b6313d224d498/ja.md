```
translate(r::Run, x::Integer, y::Integer)
translate(r::Run, a::Vector{Int64})
```

ランを移動します。移動は、行と列にオフセットを追加することによって行われます。

translate メソッドに加えて、+ または - 演算子を使用してランを移動することもできます。

```jldoctest reg
julia> using Regions

julia> translate(Run(1, 20:30), 10, 20)
Run(21, 30:40)

julia> translate(Run(1, 2:3), [10, 20])
Run(21, 12:13)

julia> Run(1, 2:3) + [10, 20]
Run(21, 12:13)

julia> [1, 2] + Run(0, 0:10)
Run(2, 1:11)

julia> Run(0, 0:100) - [5, 25]
Run(-25, -5:95)
```
