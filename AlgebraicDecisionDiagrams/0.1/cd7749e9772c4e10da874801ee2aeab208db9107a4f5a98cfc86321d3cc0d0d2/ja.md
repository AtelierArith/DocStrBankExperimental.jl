```
apply(OP,α,β,opcache,vcache)
```

再帰的にα OP βを計算し、結果をキャッシュします。

# パラメータ

  * `OP`: 葉に適用する操作
  * `α`,`β`: 決定図
  * `opcache`: 適用された操作のキャッシュ
  * `vcache`: 終端値のキャッシュ
