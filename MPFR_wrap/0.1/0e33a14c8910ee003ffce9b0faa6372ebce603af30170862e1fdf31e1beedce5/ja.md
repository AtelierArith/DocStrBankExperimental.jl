```
acos!(rop, op, rnd)
```

`rop`を`op`の逆余弦に設定し、方向`rnd`で丸めます。`acos(-1)`は、指定された丸めモードに従ってπに最も近い浮動小数点数を返すため、この数は逆余弦関数の出力範囲`0≤rop<π`に含まれない可能性があります。それでも、結果は丸め関数による出力範囲の像にあります。
