```
log2!(rop, op, rnd)
```

`rop`を`op`のlog₂に設定し、`rnd`の方向に丸めます。`op`が1の場合、すべての丸めモードで一貫性を保つために、`rop`を+0に設定します。`op`が±0の場合（すなわち、ゼロの符号は結果に影響を与えません）、`rop`を−Infに設定します。
