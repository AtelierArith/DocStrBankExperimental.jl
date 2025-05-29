```
gather!(rcv,snd;destination=MAIN)
```

[`gather`](@ref) のインプレースバージョンです。`rcv` を返します。結果の配列 `rcv` は、ヘルパー関数 [`allocate_gather`](@ref) を使用して割り当てることができます。
