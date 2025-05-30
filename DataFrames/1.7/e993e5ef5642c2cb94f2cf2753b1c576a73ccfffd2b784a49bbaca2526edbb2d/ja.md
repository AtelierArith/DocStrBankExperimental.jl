```
allcombinations(DataFrame, pairs::Pair...)
allcombinations(DataFrame; kwargs...)
```

渡された引数のすべての組み合わせから `DataFrame` を作成します。最初に渡された値が最も早く変化します。

列名と展開する値を関連付ける引数は、位置引数として渡された `Pair` として指定するか、キーワード引数として指定できます。列名は `Symbol` または文字列でなければならず、一意である必要があります。

列の値は、そのまま消費されるベクターであるか、他の任意の型のオブジェクト（`AbstractArray` を除く）であることができます。後者の場合、渡された値は展開のために長さ1を持つものとして扱われます。特に、`Ref` に格納された値や `0` 次元の `AbstractArray` はアンラップされ、長さ1を持つものとして扱われます。

また、[`crossjoin`](@ref) を使用して、渡されたデータフレームの行の直積を取得することができます。

# 例

```jldoctest
julia> allcombinations(DataFrame, a=1:2, b='a':'c')
6×2 DataFrame
 Row │ a      b
     │ Int64  Char
─────┼─────────────
   1 │     1  a
   2 │     2  a
   3 │     1  b
   4 │     2  b
   5 │     1  c
   6 │     2  c

julia> allcombinations(DataFrame, "a" => 1:2, "b" => 'a':'c', "c" => "const")
6×3 DataFrame
 Row │ a      b     c
     │ Int64  Char  String
─────┼─────────────────────
   1 │     1  a     const
   2 │     2  a     const
   3 │     1  b     const
   4 │     2  b     const
   5 │     1  c     const
   6 │     2  c     const
```
