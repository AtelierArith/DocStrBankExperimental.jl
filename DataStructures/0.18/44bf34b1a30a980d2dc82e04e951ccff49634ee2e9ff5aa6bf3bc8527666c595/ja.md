```
RobinDict([itr])
```

`RobinDict{K,V}()` は、型 `K` のキーと型 `V` の値を持つハッシュテーブルを構築します。キーは [`isequal`](@ref) で比較され、[`hash`](@ref) でハッシュ化されます。単一のイテラブル引数が与えられると、引数によって生成された2タプル `(key,value)` からキーと値のペアを取る [`RobinDict`](@ref) を構築します。

# 例

```jldoctest
julia> RobinDict([("A", 1), ("B", 2)])
RobinDict{String, Int64} with 2 entries:
  "B" => 2
  "A" => 1
```

また、ペア引数のシーケンスを渡すこともできます。

```jldoctest
julia> RobinDict("A"=>1, "B"=>2)
RobinDict{String, Int64} with 2 entries:
  "B" => 2
  "A" => 1
```
