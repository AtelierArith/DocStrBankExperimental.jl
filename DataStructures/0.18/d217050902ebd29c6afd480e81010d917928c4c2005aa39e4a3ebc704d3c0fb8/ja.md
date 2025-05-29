```
SwissDict([itr])
```

`SwissDict{K,V}()` は、型 `K` のキーと型 `V` の値を持つハッシュテーブルを構築します。キーは [`isequal`](@ref) で比較され、[`hash`](@ref) でハッシュ化されます。単一のイテラブル引数が与えられると、引数によって生成された 2-タプル `(key,value)` からキーと値のペアを取る [`SwissDict`](@ref) を構築します。

# 例

```jldoctest
julia> SwissDict([("A", 1), ("B", 2)])
SwissDict{String, Int64} with 2 entries:
  "A" => 1
  "B" => 2
```

また、ペア引数のシーケンスを渡すこともできます。

```jldoctest
julia> SwissDict("A"=>1, "B"=>2)
SwissDict{String, Int64} with 2 entries:
  "A" => 1
  "B" => 2
```
