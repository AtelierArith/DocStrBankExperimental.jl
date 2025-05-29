```
ViewArray(parent, indices)
```

親の遅延ビューである配列 `out` を作成します。`out` のインデックスは `indices` のインデックスと一致し、`indices` の値は `parent` をインデックスするために使用されます。`SubArray` とは異なり、親の型は任意のインデックス可能なコンテナである可能性があります（たとえば、`AbstractDict` に格納された値の `AbstractArray` ビューを作成できます）。

`ViewDict`、`view` も参照してください。

# 例

```julia
julia> d = Dict(:a => 11, :b => 12, :c => 13)
Dict{Symbol,Int64} with 3 entries:
  :a => 11
  :b => 12
  :c => 13

julia> ViewArray(d, [:a, :c])
2-element ViewArray{Int64,1,Dict{Symbol,Int64},Array{Symbol,1}}:
 11
 13
```
