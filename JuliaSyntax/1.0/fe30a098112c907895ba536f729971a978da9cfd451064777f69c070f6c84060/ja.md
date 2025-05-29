```
parse!(TreeType, io::IO; rule=:all, version=VERSION)
```

シーケンシャブルな `IO` オブジェクトから Julia ソースコードを解析します。出力はタプル `(tree, diagnostics)` です。`parse!` が返ると、ストリーム `io` は解析中に消費された最後のバイトの直後に位置しています。
