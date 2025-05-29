```
LengthChannel(f::Function, channel::LengthChannel; kwargs...)
LengthChannel{T}(f::Function, channel::LengthChannel; kwargs...)
```

チャネルを新しいチャネルでラップし、元のチャネルの各要素に `f` を適用します。これは、例えば、内部チャネルが別のスレッドでデータを読み取り前処理できるように `spawn=true` を使用しながら、ラッパーチャネルがメインスレッドで動作するように強制するのに役立ちます。これは、スレッドセーフでない `f`、特にデータをGPUに置く `f=cu` または `f=gpu` に必要です。

チャネルをラップする際に `T` が省略されると、`f(eltype(dataset)) == typeof(f(::eltype(dataset)))` であると仮定されます。言い換えれば、`f` はラップされたチャネルの要素に `f` を適用した結果の型を返すメソッドを持っている必要があります。
