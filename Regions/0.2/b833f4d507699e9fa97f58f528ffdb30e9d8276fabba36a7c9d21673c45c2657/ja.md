```
invert(x::Run)
```

ランを反転させます。反転は、原点でランを鏡映します。ランは、その行を否定し、列を反転させることによって反転されます。

invert メソッドに加えて、単項 - 演算子も使用できます。

```jldoctest reg
julia> using Regions

julia> invert(Run(1, 20:30))
Run(-1, -30:-20)

julia> -Run(-1, -30:-20)
Run(1, 20:30)
```
