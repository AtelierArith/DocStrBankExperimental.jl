```
@pgf { ... }

@pgf some(nested(form({ ... })),
          with_multiple_options({ ... }))
```

カンマ区切りの `key`（値なし）、`key = value`、`key : value`、または `key => value` のペアを `{ ... }` で囲んで、式のどこにでも [`Options`](@ref) を構築します。

キーは次のようになります。

1. シンボルは文字列に変換され、`_` がスペースに置き換えられます。
2. 文字列または生文字列はそのまま使用されます。

引数は再帰的にトラバースされ、複数の場所に `{ ... }` 表現を含むことができます。

複数の単語からなるキーは、引用符で囲むか、アンダースコアを含む文字列として書く必要があります。

```julia
@pgf {
    "only marks",
    mark_size = "0.6pt",
    mark = "o",
    color => "black",
}
```

別の `Options` を `...` を使用して作成中のものにスプライスできます。例えば、

```
theme = @pgf {xmajorgrids, x_grid_style = "white"}

axis_opt = @pgf {theme..., title = "My figure"}
```

空のオプションには `{}` を使用し、LaTeX では `[]` として印刷されます。
