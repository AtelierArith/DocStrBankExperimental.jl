```
sound(x::AbstractMatrix, S::Real = framerate(x) [, output_device])
```

デフォルトのオーディオ出力デバイスを使用して、サンプリングレート `S` サンプル/秒でステレオオーディオ信号 `x` を再生します。呼び出し元は、`x` に対して `framerate` メソッドが定義されていない限り、`S` を指定する必要があります。
