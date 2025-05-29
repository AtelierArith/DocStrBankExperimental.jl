```
s = format(unit::Unit; names = false, definition = false)
```

単位 `unit` を文字列としてフォーマットします。names が true の場合、definition は単位名（例：メートル）を使用し、記号（例：m）ではなくなります。definition が true の場合、単位は基本単位で表現されるべきです（W の代わりに m²·kg·s⁻³）。
