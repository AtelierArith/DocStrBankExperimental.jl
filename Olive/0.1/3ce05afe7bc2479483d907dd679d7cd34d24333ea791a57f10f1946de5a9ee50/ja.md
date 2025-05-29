```
build(c::Connection, cell::Cell{<:Any}, d::Directory{<:Any}) -> ::Component{:div}
```

ディレクトリセルのためのキャッチオール/デフォルトの `build` 関数。この関数は、Olive がディレクトリ内で読み取れないファイルのために灰色のボックスを作成します。この関数をテンプレートとして使用することで、自分自身のディレクトリセルを作成できます。この関数の新しいメソッドを書いて、新しいファイルタイプのセルを構築してください。新しいファイルタイプを保存するために `olive_save` を拡張することも考慮してください。`dblclick` をバインドし、`explorer` に依存して `load_session` または `add_to_session` メソッドを使用します... これはデフォルトで `false` であるべきです。`directory_cells` はファイルパスを `cell.outputs` に、ファイル名を `cell.source` に入れます。

```julia

```

ファイルセルを作成するために見るべき他の**重要な**関数は次のとおりです：

  * `build_base_cell`
  * `evaluate`
  * `olive_save`
  * `olive_read`
