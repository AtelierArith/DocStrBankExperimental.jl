```
rydberg_corr([op=Op.n], reg) -> Matrix
```

ライデンバーグ相関行列を計算します。

$$
\langle \text{op}_i \text{op}_j \rangle
$$

ここで `op` は `Op.n`、`X` または `Y` です。

# 引数

  * `op`: 相関関数、デフォルトは `Op.n` です。
  * `reg`: 必須、レジスタオブジェクトです。
