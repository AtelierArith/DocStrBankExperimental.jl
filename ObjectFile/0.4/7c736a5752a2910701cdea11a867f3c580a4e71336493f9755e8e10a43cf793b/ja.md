```
symtab_entry_type(oh::ObjectHandle)
```

`ObjectHandle`を指定すると、シンボルテーブルエントリのタイプを返します（`SymtabEntry`オブジェクトを読み込もうとしたり、`Symbols`オブジェクトを反復処理する際にシンボルテーブルを読み込むために使用されます）。たとえば、64ビットELFファイルの場合、これはタイプ`ELFSymtabEntry64`を返します。
