```
evaluate!(dest, input, time, args...; kwargs...)
```

指定された `time` で `input` を評価し、出力を `dest` にインプレースで書き込みます。

`input` の詳細に応じて、この関数は I/O および通信を行う場合があります。

# 追加の引数

`args` と `kwargs` は、`input` が非補間関数（例えば、解析関数）の場合にのみ使用されます。その場合、`args` と `kwargs` は関数自体に渡されます。
