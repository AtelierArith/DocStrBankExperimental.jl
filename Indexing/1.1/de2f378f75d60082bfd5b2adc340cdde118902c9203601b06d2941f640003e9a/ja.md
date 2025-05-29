getindices(container, indices)

インデックス `keys(indices)` を持ち、値 `container[i]` を持つインデックス可能なコンテナを返します。ここで、`i ∈ values(indices)` です。これは、辞書、タプル、名前付きタプルなどの複数のインデックスに対してスカラー `getindex(container, index)` を一般化したものです。

# 例

```julia
julia> d = Dict(:a => "Alice", :b => "Bob", :c => "Charlie")
Dict{Symbol,String} with 3 entries:
  :a => "Alice"
  :b => "Bob"
  :c => "Charlie"

julia> getindices(d, [:a, :c])
2-element Array{String,1}:
 "Alice"  
 "Charlie"

julia> getindices(d, (:a, :c))
("Alice", "Charlie")

julia> getindices(d, Dict("Wife" => :a, "Husband" => :c))
Dict{String,String} with 2 entries:
  "Wife"    => "Alice"
  "Husband" => "Charlie"
```
