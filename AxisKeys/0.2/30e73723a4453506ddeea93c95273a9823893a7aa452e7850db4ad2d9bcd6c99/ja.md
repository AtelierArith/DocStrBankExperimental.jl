```
wrapdims(table, value, names...; default=undef, sort=false, force=false)
```

`KeyedArray(NamedDimsArray(A,names),keys)`を、[Tables.jl](https://github.com/JuliaData/Tables.jl) APIに一致する`table`から構築します。（`Tables.columns`と`Tables.rows`の両方をサポートする必要があります。）

配列の内容は、テーブルの列`value::Symbol`から取得されます。`names`の各シンボルは、ユニークなエントリが配列の次元のキーとなる列を指定します。

テーブルに可能なキーのセットに一致する行がない場合、この配列の要素は未定義になります。ただし、`default`キーワードを提供すれば例外です。複数の行が同じキーのセットを共有する場合、デフォルトでは`ArgumentError`がスローされます。キーワード`force=true`を指定すると、これらの非ユニークなエントリが上書きされます。

同様の方法で既存の配列を埋めるために[`populate!`](@ref)も参照してください。

`AxisKeys.nameouter() = false`を設定すると、生成されるラッパーの順序が逆になります。

# 例

```jldoctest
julia> using DataFrames, AxisKeys

julia> df = DataFrame("a" => 1:3, "b" => 10:12.0, "c" => ["cat", "dog", "cat"])
3×3 DataFrame
 Row │ a      b        c      
     │ Int64  Float64  String 
─────┼────────────────────────
   1 │     1     10.0  cat
   2 │     2     11.0  dog
   3 │     3     12.0  cat

julia> wrapdims(df, :a, :b, :c; default=missing)
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   b ∈ 3-element Vector{Float64}
→   c ∈ 2-element Vector{String}
And data, 3×2 Matrix{Union{Missing, Int64}}:
         ("cat")    ("dog")
 (10.0)   1           missing
 (11.0)    missing   2
 (12.0)   3           missing

julia> wrapdims(df, :a, :b)
1-dimensional NamedDimsArray(KeyedArray(...)) with keys:
↓   b ∈ 3-element Vector{Float64}
And data, 3-element Vector{Union{Missing, Int64}}:
 (10.0)  1
 (11.0)  2
 (12.0)  3

julia> wrapdims(df, :a, :c)
ERROR: ArgumentError: Key ("cat",) is not unique

julia> wrapdims(df, :a, :c, force=true)
1-dimensional NamedDimsArray(KeyedArray(...)) with keys:
↓   c ∈ 2-element Vector{String}
And data, 2-element Vector{Int64}:
 ("cat")  3
 ("dog")  2
```
