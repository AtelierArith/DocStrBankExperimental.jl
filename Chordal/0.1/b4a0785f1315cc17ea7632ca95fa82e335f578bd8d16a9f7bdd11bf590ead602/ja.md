```
make_selectors_from_clique_graph(cg::CliqueGraph, n)
```

`n` 頂点を持つ CliqueGraph `cg` からセレクタ行列 `Tℓ` を構築します。

`Tℓ*X*Tℓ'` は、クリーク `ℓ` に対応する `X` の部分行列です。
