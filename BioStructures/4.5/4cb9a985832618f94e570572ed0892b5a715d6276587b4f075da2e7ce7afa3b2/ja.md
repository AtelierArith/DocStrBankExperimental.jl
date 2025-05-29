```
writemmcif(output, element, atom_selectors...; gzip=false)
writemmcif(output, mmcif_dict; gzip=false)
```

`StructuralElementOrList` または `MMCIFDict` を mmCIF 形式のファイルまたは出力ストリームに書き込みます。

原子セレクタ関数は追加の引数として指定できます - すべての関数から `true` を返す原子のみが保持されます。キーワード引数 `expand_disordered`（デフォルトは `true`）は、無秩序な残基と原子のすべてのコピーを返すかどうかを決定します。キーワード引数 `gzip`（デフォルトは `false`）は、出力が gzipped されるかどうかを決定します。
