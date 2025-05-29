```
@rename!(d, args...)
```

列名のインプレース修正。

### 引数

  * `d` : AbstractDataFrame
  * `args...` : 列名の変更を指定する `:new = :old` の形式の式

"old" から "new" へ。各式の左辺と右辺は、`:old_col` のようなシンボル引数として、または `$"new_col"` のように `$` でエスケープされた文字列として渡すことができます。受け入れられる値の説明については **詳細** を参照してください。

### 戻り値

  * `::AbstractDataFrame`

`@rename!` への入力は、`begin ... end` ブロックまたは一連のキーワードのような引数の形式で提供できます。たとえば、以下は同等です：

```julia
@rename! df begin
    :new_col = :old_col
end
```

および

```
@rename!(df, :new_col = :old_col)
```

### 詳細

列名の割り当てを指定する式の左辺と右辺は、`Symbol` または `$` でエスケープされた `String` のいずれかであることができます。たとえば、`:new = ...` と `$"new" = ...` は、新しい列名を割り当てるための有効な方法です。

このアイデアは、任意の右辺の式を渡すために拡張できます。たとえば、以下は同等です：

```
@rename!(df, :new = :old1)
```

および

```
@rename!(df, :new = old_col1)
```

### 例

```
julia> df = DataFrame(old_col1 = rand(5), old_col2 = rand(5),old_col3 = rand(5));

julia> @rename!(df, :new1 = :old_col1)
5×3 DataFrame
 Row │ new1       old_col2   old_col3
     │ Float64    Float64    Float64
─────┼────────────────────────────────
   1 │ 0.0176206  0.493592   0.348072
   2 │ 0.861545   0.512254   0.85763
   3 │ 0.263082   0.0267507  0.696494
   4 │ 0.643179   0.299391   0.780125
   5 │ 0.731267   0.18905    0.767292

julia> df = DataFrame(old_col1 = rand(5), old_col2 = rand(5),old_col3 = rand(5));

julia> @rename!(df, :new1 = :old_col1, :new2 = $"old_col2")
5×3 DataFrame
 Row │ new1       new2       old_col3
     │ Float64    Float64    Float64
─────┼────────────────────────────────
   1 │ 0.0176206  0.493592   0.348072
   2 │ 0.861545   0.512254   0.85763
   3 │ 0.263082   0.0267507  0.696494
   4 │ 0.643179   0.299391   0.780125
   5 │ 0.731267   0.18905    0.767292

julia> df = DataFrame(old_col1 = rand(5), old_col2 = rand(5),old_col3 = rand(5));

julia> @rename!(df, :new1 = $("old_col" * "1"), :new2 = :old_col2)
5×3 DataFrame
 Row │ new1       new2       old_col3
     │ Float64    Float64    Float64
─────┼────────────────────────────────
   1 │ 0.0176206  0.493592   0.348072
   2 │ 0.861545   0.512254   0.85763
   3 │ 0.263082   0.0267507  0.696494
   4 │ 0.643179   0.299391   0.780125
   5 │ 0.731267   0.18905    0.767292
```
