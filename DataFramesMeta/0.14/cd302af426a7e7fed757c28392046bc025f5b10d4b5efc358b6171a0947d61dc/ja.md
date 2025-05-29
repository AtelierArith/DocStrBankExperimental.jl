```
@rename(d, args...)
```

列名を変更します。

### 引数

  * `d` : AbstractDataFrame
  * `args...` : 列名の変更を指定する `:new = :old` の形式の式

"old" から "new" へ。各式の左辺と右辺は、`:old_col` のようなシンボル引数として、または `$"new_col"` のように `$` でエスケープされた文字列として渡すことができます。受け入れられる値の説明については **詳細** を参照してください。

### 戻り値

  * `::AbstractDataFrame`

`@rename` への入力は、`begin ... end` ブロックまたは一連のキーワードのような引数の形式で提供できます。たとえば、以下は同等です：

```julia
@rename df begin
    :new_col = :old_col
end
```

および

```
@rename df :new_col = :old_col
@rename(df, :new_col = :old_col)
```

### 詳細

列名の割り当てを指定する式の左辺と右辺は、`Symbol` または `$` でエスケープされた `AbstractString`（空白を含む可能性があります）であることができます。たとえば、`:new = ...` と `$"new" = ...` は、新しい列名を割り当てるための有効な方法です。

このアイデアは、任意の右辺の式を渡すために拡張できます。たとえば、以下は同等です：

```
@rename(df, :new = :old1)
```

および

```
@rename(df, :new = old_col1)
```

右辺は、列の位置を示すために `$` でエスケープされた `Integer` であることもできます。たとえば、データフレームの4番目の列の名前を新しい名前に変更するには、`@rename df :newname = $` と書きます。

### 例

```
julia> df = DataFrame(old_col1 = 1:5, old_col2 = 11:15, old_col3 = 21:25);

julia> @rename(df, :new1 = :old_col1)
5×3 DataFrame
 Row │ new1   old_col2  old_col3
     │ Int64  Int64     Int64
─────┼───────────────────────────
   1 │     1        11        21
   2 │     2        12        22
   3 │     3        13        23
   4 │     4        14        24
   5 │     5        15        25

julia> @rename(df, :new1 = :old_col1, :new2 = $"old_col2")
5×3 DataFrame
 Row │ new1   new2   old_col3
     │ Int64  Int64  Int64
─────┼────────────────────────
   1 │     1     11        21
   2 │     2     12        22
   3 │     3     13        23
   4 │     4     14        24
   5 │     5     15        25

julia> @rename(df, :new1 = $("old_col" * "1"), :new2 = :old_col2)
5×3 DataFrame
 Row │ new1   new2   old_col3
     │ Int64  Int64  Int64
─────┼────────────────────────
   1 │     1     11        21
   2 │     2     12        22
   3 │     3     13        23
   4 │     4     14        24
   5 │     5     15        25

julia> @rename df $("New with spaces") = :old_col1
5×3 DataFrame
 Row │ New with spaces  old_col2  old_col3
     │ Int64            Int64     Int64
─────┼─────────────────────────────────────
   1 │               1        11        21
   2 │               2        12        22
   3 │               3        13        23
   4 │               4        14        24
   5 │               5        15        25

julia> @rename df :new_col2 = $2
5×3 DataFrame
 Row │ old_col1  new_col2  old_col3
     │ Int64     Int64     Int64
─────┼──────────────────────────────
   1 │        1        11        21
   2 │        2        12        22
   3 │        3        13        23
   4 │        4        14        24
   5 │        5        15        25
```
