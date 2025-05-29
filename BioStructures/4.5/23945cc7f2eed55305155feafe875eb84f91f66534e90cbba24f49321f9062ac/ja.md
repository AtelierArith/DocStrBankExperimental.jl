```
writepdb(output, element, atom_selectors...)
```

`StructuralElementOrList`をProtein Data Bank (PDB)フォーマットのファイルまたは出力ストリームに書き込みます。

ATOM、HETATM、MODEL、およびENDMDLレコードのみが書き込まれます - ヘッダーはなく、TERレコードもありません。原子セレクタ関数は追加の引数として指定できます - すべての関数から`true`を返す原子のみが保持されます。キーワード引数`expand_disordered`（デフォルトは`true`）は、無秩序な残基と原子のすべてのコピーを返すかどうかを決定します。
