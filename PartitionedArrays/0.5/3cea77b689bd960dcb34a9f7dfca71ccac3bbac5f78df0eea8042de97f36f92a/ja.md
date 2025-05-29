```
scatter!(rcv,snd;source=1)
```

[`scatter`](@ref) のインプレースバージョンです。宛先配列 `rcv` は、ヘルパー関数 [`allocate_scatter`](@ref) を使用して生成できます。これにより `rcv` が返されます。
