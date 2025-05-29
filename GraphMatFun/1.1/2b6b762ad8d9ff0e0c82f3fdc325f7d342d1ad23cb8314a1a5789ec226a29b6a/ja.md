```
(graph,cref)=graph_sastre_exp(k,method=:auto)
```

`k` 行列の乗算に従って指数関数を近似する多項式評価を計算します。`method` は参照に記載されています。スキームは `degop` 形式に埋め込まれています。詳細は [`graph_degopt`](@ref) を参照してください。

方法は以下の通りです（下記の論文から）：

  * `:ps_degopt`、Paterson–Stockmeyer 法が `degopt` 形式に埋め込まれています。
  * `:y1s`、式 (34)-(35) による
  * `:z1ps`、式 (34)-(35) および (52) による
  * `:h2m`、式 (34)-(35) および (69) による

`k` と `method` のすべての組み合わせが実装されているわけではありません。利用可能なものは以下の通りです：

  * `k<3`、`method`=`:ps_degopt`
  * `k=3`、`method`=`:y1s`、参照の表 4 に従う
  * `k=4`、`method`=`:y1s`
  * `k=6`、`method`=`:h2m`、参照の表 11 に従う
  * `k=8`、`method`=`:z1ps`、参照の表 7 に従う

デフォルトオプション `method=:auto` は、上記のように `k` の値に応じて方法を選択します。

**参考文献**

1. J. Sastre. "Efficient evaluation of matrix polynomials". Linear Algebra and its Applications, 539:229-250, 2018. DOI: [10.1016/j.laa.2017.11.010](https://doi.org/10.1016/j.laa.2017.11.010)
