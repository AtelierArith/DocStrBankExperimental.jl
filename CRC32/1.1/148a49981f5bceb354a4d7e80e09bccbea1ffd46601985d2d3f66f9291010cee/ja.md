```
crc32(io::IO, [nb::Integer,] crc::UInt32=0x00000000)
```

`io` から最大 `nb` バイトを読み取り、オプションで開始 `crc` 整数と混合された CRC-32 チェックサムを返します。 `nb` が指定されていない場合、`io` はストリームの終わりまで読み取られます。
