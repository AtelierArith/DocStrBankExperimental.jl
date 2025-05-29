```
section_header_type(oh::ObjectHandle)
```

`ObjectHandle`を与えると、セクションヘッダーのタイプを返します（`Section`オブジェクトを読み込む際や`Sections`オブジェクトを反復処理する際にセクションヘッダーを読み込むために使用されます）。例えば、64ビットELFファイルの場合、これはタイプ`ELFSection64`を返します。
