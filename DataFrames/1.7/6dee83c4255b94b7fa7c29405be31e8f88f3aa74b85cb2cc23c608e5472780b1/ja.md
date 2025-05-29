```
DataFrameRow{<:AbstractDataFrame, <:AbstractIndex}
```

`AbstractDataFrame`の1行のビュー。

`DataFrameRow`は、1行と列の選択が要求されたとき、または[`eachrow`](@ref)関数の呼び出しの結果を反復処理するときに、`getindex`または`view`関数によって返されます。

`DataFrameRow`コンストラクタは直接呼び出すこともできます：

```
DataFrameRow(parent::AbstractDataFrame, row::Integer, cols=:)
```

`DataFrameRow`は反復インターフェースをサポートしているため、コレクションを引数として期待する関数に渡すことができます。その要素の型は常に`Any`です。

インデックスは1次元で、`DataFrame`の列を指定するようになっています。また、`getproperty`および`setproperty!`関数を使用して`DataFrameRow`内のデータにアクセスし、対応する関数を使用して`Tuple`、`NamedTuple`、または`Vector`に変換することもできます。

親データフレームの列の選択が`:`（コロン）として渡されると、`DataFrameRow`は常に親からのすべての列を持ち、その作成後に追加または削除されても変わりません。

# 例

```jldoctest
julia> df = DataFrame(a=repeat([1, 2], outer=[2]),
                      b=repeat(["a", "b"], inner=[2]),
                      c=1:4)
4×3 DataFrame
 Row │ a      b       c
     │ Int64  String  Int64
─────┼──────────────────────
   1 │     1  a           1
   2 │     2  a           2
   3 │     1  b           3
   4 │     2  b           4

julia> df[1, :]
DataFrameRow
 Row │ a      b       c
     │ Int64  String  Int64
─────┼──────────────────────
   1 │     1  a           1

julia> @view df[end, [:a]]
DataFrameRow
 Row │ a
     │ Int64
─────┼───────
   4 │     2

julia> eachrow(df)[1]
DataFrameRow
 Row │ a      b       c
     │ Int64  String  Int64
─────┼──────────────────────
   1 │     1  a           1

julia> Tuple(df[1, :])
(1, "a", 1)

julia> NamedTuple(df[1, :])
(a = 1, b = "a", c = 1)

julia> Vector(df[1, :])
3-element Vector{Any}:
 1
  "a"
 1
```
