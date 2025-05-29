```
set_chunk_defaults!(k, v)
set_chunk_defaults!(kv::Pair...)
set_chunk_defaults!(opts::AbstractDict)
```

コードチャンクのデフォルトオプションを設定します。現在の値を確認するには [`get_chunk_defaults`](@ref) を使用してください。

例えば、以下の3つの例はすべてデフォルトの `dpi` を `200` に、`fig_width` を `8` に設定します：

  * `set_chunk_defaults!(:dpi, 200); set_chunk_defaults!(:fig_width, 8)`
  * `set_chunk_defaults!(:dpi => 200, :fig_width => 8)`
  * `set_chunk_defaults!(Dict(:dpi => 200, :fig_width => 8))`
