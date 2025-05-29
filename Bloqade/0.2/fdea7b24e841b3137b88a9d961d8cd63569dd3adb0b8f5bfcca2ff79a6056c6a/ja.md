```
bitstring_hist!(ax, register; nlargest::Int, title="", kw...)
```

ビットストリングのヒストグラムをプロットします。

# 引数

  * `ax`: `CairoMakie`からの軸オブジェクト。
  * `register`: プロットするレジスタ。

# キーワード引数

  * `nlargest`: 最初の `nlargest` ビットストリングをプロットします。
  * `title`: プロットのタイトル。
  * `kw`: `CairoMakie.bars!` 関数がサポートするその他のキーワード引数。
