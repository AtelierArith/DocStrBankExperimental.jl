```
segment_header_type(oh::ObjectHandle)
```

`ObjectHandle`を与えると、セグメントヘッダーのタイプを返します（`Segment`オブジェクトを読み込む際や`Segments`オブジェクトを反復処理する際にセグメントヘッダーを読み込むために使用されます）。例えば、64ビットELFファイルの場合、これはタイプ`ELFSegment64`を返します。
