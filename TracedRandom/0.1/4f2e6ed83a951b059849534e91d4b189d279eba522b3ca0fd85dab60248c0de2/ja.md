```
shuffle!([rng=GLOBAL_RNG,] addr::Address, args...)
```

`shuffle!`のトレース実行。ここで、`addr`はランダムな選択の名前/アドレスを指定します。デフォルトでは、アドレス`addr`は無視されますが、確率的プログラミングシステムでの推論をサポートするためにインターセプトすることができます。`Address`は`Symbol`または`Symbol`で始まる`Pair`のいずれかです。
