```
nls_meta(nls)
```

`nls`の`nls_meta`構造体を返します。内部モデルを持つモデルを扱うために、`nls.nls_meta`の代わりにこれを使用してください。

基本モデルに対しては`nls_meta(nls)`は`nls.nls_meta`として定義されていますが、複合モデルは`nls_meta`を保持しない可能性があるため、`nls.internal.nls_meta`のように特化されることがあります。
