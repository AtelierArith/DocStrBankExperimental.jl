```
multicast!(rcv,snd;source=1)
```

[`multicast`](@ref) のインプレースバージョンです。宛先配列 `rcv` は、ヘルパー関数 [`allocate_multicast`](@ref) を使用して生成できます。`rcv` を返します。
