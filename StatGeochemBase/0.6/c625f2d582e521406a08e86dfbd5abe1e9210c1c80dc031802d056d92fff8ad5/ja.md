```julia
concatenatedatasets(d1::NamedTuple, d2::NamedTuple,... ;[elements::Vector{Symbol}])
concatenatedatasets(d1::AbstractDict, d2::AbstractDict,... ;[elements::Vector{String}])
```

2つ以上のDictまたはTupleベースのデータセットを、変数ごとに縦に連結します。オプションで、`elements`で含める変数のリストを指定できます。

### 例

```julia
julia> d1 = Dict("La" => rand(5), "Yb" => rand(5))
Dict{String, Vector{Float64}} with 2 entries:
  "Yb" => [0.221085, 0.203369, 0.0657271, 0.124606, 0.0975556]
  "La" => [0.298578, 0.481674, 0.888624, 0.632234, 0.564491]

julia> d2 = Dict("La" => rand(5), "Ce" => rand(5))
Dict{String, Vector{Float64}} with 2 entries:
  "Ce" => [0.0979752, 0.108585, 0.718315, 0.771128, 0.698499]
  "La" => [0.538215, 0.633298, 0.981322, 0.908532, 0.77754]

julia> concatenatedatasets(d1,d2)
Dict{String, Vector{Float64}} with 3 entries:
  "Ce" => [NaN, NaN, NaN, NaN, NaN, 0.0979752, 0.108585, 0.718315, 0.771128, 0.698499]
  "Yb" => [0.221085, 0.203369, 0.0657271, 0.124606, 0.0975556, NaN, NaN, NaN, NaN, NaN]
  "La" => [0.298578, 0.481674, 0.888624, 0.632234, 0.564491, 0.538215, 0.633298, 0.981322, 0.908532, 0.77754]
```
