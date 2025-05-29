```
Double64(x::Double32)
```

`Double32`を`Double64`に昇格させるには、`x`の`hi`および`lo`属性を`Double64`に変換し、拡張精度で加算します。
