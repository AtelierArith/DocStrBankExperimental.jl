```julia
build(c::Connection, cm::ComponentModifier, cell::Cell{<:Any},
proj::Project{<:Any}) -> ::Component{:div}
```

セッションセルのためのキャッチオール/デフォルトの `build` 関数。この関数は、Olive が作成できないセルのための灰色のボックスを作成します。この関数をテンプレートとして使用することで、自分自身のオリーブセルを作成できます。

```

```

セルにとっても重要なこと:

  * `cell_bind!`
  * `build_base_cell`
  * `evaluate`
  * `ToolipsSession.bind`
  * `cell_highlight!`
  * `olive_save`
  * `string`

そして、コードセルは以下で拡張できます:

  * `on_code_evaluate`
  * `on_code_highlight`
  * `on_code_build`
