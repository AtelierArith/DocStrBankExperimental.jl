```
y1!(rop, op, rnd)
```

`rop`を`op`の0次のベッセル関数の値に設定し、方向`rnd`で丸めます。`op`がNaNまたは負の場合、`rop`は常にNaNに設定されます。`op`が+Infの場合、`rop`は+0に設定されます。`op`がゼロの場合、`rop`は-Infinityに設定されます。
