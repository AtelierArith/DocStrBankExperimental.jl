```
OrderedRobinDict([itr])
```

`OrderedRobinDict{K,V}()` は、キーの型 `K` と値の型 `V` を持つ順序付き辞書を構築します。キーの順序を維持するために `RobinDict` を利用しています。単一の反復可能な引数を与えると、引数によって生成された2タプル `(key,value)` からキーと値のペアを取った [`OrderedRobinDict`](@ref) を構築します。

# 例

```jldoctest
julia> OrderedRobinDict([("A", 1), ("B", 2)])
OrderedRobinDict{String, Int64} with 2 entries:
  "A" => 1
  "B" => 2
```

また、ペアの引数のシーケンスを渡すこともできます。

```jldoctest
julia> OrderedRobinDict("A"=>1, "B"=>2)
OrderedRobinDict{String, Int64} with 2 entries:
  "A" => 1
  "B" => 2
```
