```
randsubseq([rng=GLOBAL_RNG,] addr::Address, args...)
```

`randsubseq`のトレース実行。ここで、`addr`はランダム選択の名前/アドレスを指定します。デフォルトでは、アドレス`addr`は無視されますが、確率的プログラミングシステムでの推論をサポートするためにインターセプトすることができます。`Address`は`Symbol`であるか、`Symbol`で始まる`Pair`です。
