```
randperm!([rng=GLOBAL_RNG,] addr::Address, args...)
```

`randperm!`のトレース実行。ここで、`addr`はランダムな選択の名前/アドレスを指定します。デフォルトでは、アドレス`addr`は無視されますが、確率的プログラミングシステムでの推論をサポートするためにインターセプトすることができます。`Address`は`Symbol`であるか、`Symbol`で始まる`Pair`です。
