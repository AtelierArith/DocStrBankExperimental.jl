```
pack(io::IO, source, endianness::Symbol = :NativeEndian)
```

入力 `source` を `io` にパックし、`io` の指定された `endianness` に従ってバイトスワッピングを行います。`endianness` が `:NativeEndian`（デフォルト）の場合、バイトスワッピングは行われません。`endianness` が `:LittleEndian` または `:BigEndian` の場合、ホストシステムのエンディアンが `io` のエンディアンと一致しない場合にバイトスワッピングが行われます。
