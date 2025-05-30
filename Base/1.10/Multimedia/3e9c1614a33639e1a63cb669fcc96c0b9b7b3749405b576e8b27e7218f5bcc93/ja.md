```
TextDisplay(io::IO)
```

`TextDisplay <: AbstractDisplay` を返します。これは、任意のオブジェクトをテキスト/plain MIME タイプとして表示し（デフォルト）、テキスト表現を指定された I/O ストリームに書き込みます。（これは、Julia REPL でオブジェクトが印刷される方法です。）
