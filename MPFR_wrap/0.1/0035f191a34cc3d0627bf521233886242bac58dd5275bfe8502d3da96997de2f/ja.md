```
sqrt!(rop, op, rnd)
```

`rop`を`√op`に設定し、方向`rnd`で丸めます。`op`が−0の場合、`rop`を−0に設定し、IEEE 754標準に従います。`op`が負の場合はDomainError例外をスローします。
