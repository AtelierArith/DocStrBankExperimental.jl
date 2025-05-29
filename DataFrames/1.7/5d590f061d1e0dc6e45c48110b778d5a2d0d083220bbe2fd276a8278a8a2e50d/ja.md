```
filter(fun, df::AbstractDataFrame; view::Bool=false)
filter(cols => fun, df::AbstractDataFrame; view::Bool=false)
```

`fun` が `true` を返す `df` の行のみを含むデータフレームを返します。

`cols` が指定されていない場合、述語 `fun` は `DataFrameRow` を受け取ります。`DataFrameRow` の要素には、`fun` 内でドット構文または列インデックスを使用してアクセスできます。

`cols` が指定されている場合、述語 `fun` は対応する列の要素を別々の位置引数として受け取ります。ただし、`cols` が `AsTable` セレクタである場合、これらの引数の `NamedTuple` が渡されます。`cols` は任意の列セレクタ（`Symbol`、文字列または整数; `:`, `Cols`, `All`, `Between`, `Not`、正規表現、または `Symbol`、文字列または整数のベクター）であり、`Symbol`、文字列、または整数のベクターが渡された場合、列の重複が許可されます。

`view=false` の場合、新しく割り当てられた `DataFrame` が返されます。`view=true` の場合、`df` への `SubDataFrame` ビューが返されます。

`cols` を渡すことで、大きなデータフレームに対する操作の実行がより効率的になります。

!!! note
    このメソッドは、DataFrames.jl がコレクションのための Julia API を実装するように定義されていますが、他の DataFrames.jl 関数と一貫性があるため、代わりに [`subset`](@ref) 関数を使用することが一般的に推奨されます（`filter` とは対照的に）。


!!! note
    型の安定性のため、`filter(cols => fun, df::AbstractDataFrame; view::Bool=false)` の呼び出しは、パフォーマンスが重要なアプリケーションで好まれます。


メタデータ: この関数は、テーブルレベルおよび列レベルの `:note` スタイルのメタデータを保持します。

参照: [`filter!`](@ref)

# 例

```jldoctest
julia> df = DataFrame(x=[3, 1, 2, 1], y=["b", "c", "a", "b"])
4×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     3  b
   2 │     1  c
   3 │     2  a
   4 │     1  b

julia> filter(row -> row.x > 1, df)
2×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     3  b
   2 │     2  a

julia> filter(row -> row["x"] > 1, df)
2×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     3  b
   2 │     2  a

julia> filter(:x => x -> x > 1, df)
2×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     3  b
   2 │     2  a

julia> filter([:x, :y] => (x, y) -> x == 1 || y == "b", df)
3×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     3  b
   2 │     1  c
   3 │     1  b

julia> filter(AsTable(:) => nt -> nt.x == 1 || nt.y == "b", df)
3×2 DataFrame
 Row │ x      y
     │ Int64  String
─────┼───────────────
   1 │     3  b
   2 │     1  c
   3 │     1  b
```
