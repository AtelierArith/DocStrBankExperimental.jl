```
ispolyhedral(X::LazySet)
```

集合が多面体であるかどうかを確認します。

### 入力

  * `X` – 集合

### 出力

集合が多面体である場合のみ`true`を返します。

### 注意事項

回答は保守的であり、集合が多面体であっても`false`とされる場合があります。
