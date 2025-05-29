```
source_location(x)
source_location(source::SourceFile, byte_index::Integer)

source_location(LineNumberNode, x)
source_location(LineNumberNode, source, byte_index)
```

オブジェクト `x` がソース内に現れる最初のバイトの `(行, 列)` を取得します。2 番目の形式では、ソースファイルを考慮して `byte_index` をより正確に指定できます。

最初の引数として `LineNumberNode` を提供すると、行番号ノードオブジェクト内の行とファイル名が返されます。
