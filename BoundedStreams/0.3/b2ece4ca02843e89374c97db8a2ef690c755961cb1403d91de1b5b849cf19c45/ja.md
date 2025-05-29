```
BoundedInputStream(source::IO, nbytes::Integer; offset=0, close=nbytes)
```

ソースストリーム `source` を読み取るための `IO` インターフェースを提供します。バイト数を `nbytes` に制限します。`BoundedInputStream` は、作成時の位置から始まり、指定されたサイズまで拡張されるラップされたストリームのビューと見なすことができます。この領域を超えて読み取ろうとすると `EOFError` がスローされます。

オプションの整数引数 `offset` は、ソースストリームの現在の位置から開始点をシフトします。

オプションの引数 `close` は、このストリームが閉じられた後のソースストリームの位置を決定します。この場合、特別な値 `BoundedStreams.CLOSE` はソースストリームを閉じます。 ```
