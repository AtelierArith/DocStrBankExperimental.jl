```julia
TableCell(
    content; # テキスト
    textstyle = TextStyle(),
    color = nothing, # テーブル要素の背景色
    anchor = nothing, # セル内のテキストのアンカー、"top"、"bottom"、または "center" のいずれか
    lines,
    margins,
)
```

スタイル付きの TableCell をテーブル/データフレーム内で使用するために作成します。

# 例

```julia
julia> t = TableCell(4; color = :green, textstyle=(color=:blue,))
TableCell
 text is 4
 textstyle has
  color is 0000FF
 background color is 008000

```
