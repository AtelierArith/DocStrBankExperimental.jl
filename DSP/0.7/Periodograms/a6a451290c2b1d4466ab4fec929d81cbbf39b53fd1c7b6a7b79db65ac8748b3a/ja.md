```
coherence(c::Coherence)
```

`Coherence`オブジェクトを与えると、各周波数に対する各チャネル間のペアワイズコヒーレンスからなる `n_channels` x `n_channels` x `length(freq(c))` 配列を返します。
