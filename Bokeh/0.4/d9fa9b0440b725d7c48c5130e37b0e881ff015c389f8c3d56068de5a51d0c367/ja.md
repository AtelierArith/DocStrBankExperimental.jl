```
Theme(source)
```

与えられたソースからテーマを構築します。ソースは次のいずれかです：

  * [builtin theme](@ref themes) の名前。
  * JSON または YAML ファイルの名前。
  * `[type => [attr => value, ...], ...]` の形式のイテレータ。

例えば、以下はすべての図、軸、グリッド、タイトルのいくつかの属性をオーバーライドするテーマです：

```julia
Theme([
    "Figure" => [
        "background_fill_color" => "#2F2F2F",
        "border_fill_color" => "#2F2F2F",
        "outline_line_color" => "#444444",
    ],
    "Axis" => [
        "axis_line_color" => nothing,
    ],
    "Grid" => [
        "grid_line_dash" => [6, 4],
        "grid_line_alpha" => 0.3,
    ],
    "Title" => [
        "text_color" => "white",
    ],
])
```

テーマは、[`Bokeh.settings!`](@ref) を使用してグローバルに適用するか、特定のプロットに [`Document`](@ref) にラップして適用できます。
