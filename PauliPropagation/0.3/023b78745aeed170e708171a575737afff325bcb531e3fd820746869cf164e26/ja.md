```
add!(psum::PauliSum, pstr::PauliString)
```

`PauliString` `pstr` を `PauliSum` `psum` に追加します。`psum` はインプレースで変更されます。`psum` と `pstr` は同じ数のキュービットで定義されている必要があり、同じ係数型である必要があります。
