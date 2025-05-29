```
segment_header_type(oh::ELFHandle)
```

与えられたELFオブジェクト内のセグメントヘッダーの型を返します。例えば、64ビットELFオブジェクト内では、これにより`ELFSegment64`が返されます。
