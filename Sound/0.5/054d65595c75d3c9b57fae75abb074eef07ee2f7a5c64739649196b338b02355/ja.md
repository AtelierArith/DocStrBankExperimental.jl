```
sound(x::AbstractVector, S::Real = framerate(x), args...; kwargs...)
```

モノフォニックオーディオ信号 `x` をサンプリングレート `S` サンプル毎秒でデフォルトのオーディオ出力デバイスを通じて再生します。呼び出し元は `x` に対して `framerate` メソッドが定義されていない限り、`S` を指定する必要があります。
