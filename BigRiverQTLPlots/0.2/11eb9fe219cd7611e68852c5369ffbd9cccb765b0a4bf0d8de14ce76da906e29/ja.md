```
pseudotick(mytick::Vector{Float64}) => Vector{Float64}
```

新しいティックの座標を返します。連続する値のペア間の中点を返します。

## 例

```julia
julia> vticks = [1,4,5,7] |> float;

julia> pseudoticks(vticks)
4-element Vector{Float64}:
 0.5
 2.5
 4.5
 6.0

```
