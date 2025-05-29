```
unpack(io::IO, T::Type, endianness::Symbol = :NativeEndian)
```

入力 `io` を与えられた場合、型 `T` をアンパックし、`io` の指定されたエンディアンに従ってバイトスワッピングを行います。`endianness` が `:NativeEndian`（デフォルト）の場合、バイトスワッピングは行われません。`endianness` が `:LittleEndian` または `:BigEndian` の場合、ホストシステムが `io` のエンディアンと一致しない場合にエンディアンに応じたバイトスワッピングが行われます。
