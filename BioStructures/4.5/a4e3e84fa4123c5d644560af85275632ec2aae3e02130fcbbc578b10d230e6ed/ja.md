```
writemmtf(output, element, atom_selectors...; gzip=false)
writemmtf(output, mmtf_dict; gzip=false)
```

`StructuralElementOrList` または `MMTFDict` を MMTF ファイルまたは出力ストリームに書き込みます。

MMTF.jl パッケージをインポートする必要があります。原子セレクタ関数は追加の引数として指定できます - すべての関数から `true` を返す原子のみが保持されます。キーワード引数 `expand_disordered`（デフォルトは `true`）は、無秩序な残基と原子のすべてのコピーを返すかどうかを決定します。キーワード引数 `gzip`（デフォルトは `false`）は、ファイルを gzip するかどうかを決定します。
