```
bitstring_hist(r; kw...)
```

ビットストリングのヒストグラムをプロットします。

# 引数

  * `register`: プロットするレジスタ。

# キーワード引数

  * `nlargest`: 最初の `nlargest` ビットストリングをプロットします。
  * `title`: プロットのタイトル。
  * `kw...`: `CairoMakie.bars!` 関数でサポートされている他のキーワード引数。
