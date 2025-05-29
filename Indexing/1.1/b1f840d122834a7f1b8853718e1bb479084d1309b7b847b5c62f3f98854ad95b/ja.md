```
ViewDict(parent, indices)
```

配列 `out` を作成します。これは `parent` の遅延ビューです。`out` のインデックスは `indices` のインデックスと一致し、`indices` の値が `parent` をインデックスするために使用されます。親はインデックス可能な型でなければなりません - 例えば、配列や辞書です。

関連情報として `ViewArray`、`view` も参照してください。

# 例

```julia
julia> d = Dict(:a => "Alice", :b => "Bob", :c => "Charlie")
Dict{Symbol,String} with 3 entries:
  :a => "Alice"
  :b => "Bob"
  :c => "Charlie"

julia> ViewDict(d, Dict(:aa => :a, :cc => :c))
ViewDict{Symbol,String,Dict{Symbol,String},Dict{Symbol,Symbol}} with 2 entries:
  :aa => "Alice"
  :cc => "Charlie"

julia> v = [11, 12, 13]
3-element Array{Int64,1}:
 11
 12
 13

julia> ViewDict(v, Dict(:a =>1 , :c => 3))
ViewDict{Symbol,Int64,Array{Int64,1},Dict{Symbol,Int64}} with 2 entries:
  :a => 11
  :c => 13
```
