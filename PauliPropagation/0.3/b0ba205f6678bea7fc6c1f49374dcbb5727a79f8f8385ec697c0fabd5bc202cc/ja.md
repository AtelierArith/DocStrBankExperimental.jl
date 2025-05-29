```
getcoeff(psum::PauliSum{PauliStringType,CoeffType}, pstr::PauliStringType)
```

整数パウリ文字列の係数を`PauliSum`から取得します。`PauliSum`にパウリ文字列が存在しない場合はデフォルトで0になります。整数パウリ文字列`pstr`は、`psum`内の整数パウリ文字列と同じ型である必要があります。
