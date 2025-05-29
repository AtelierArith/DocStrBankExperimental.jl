```
tensor_product_operator_2D(D_x, D_y = D_x)
```

1D 微分演算子 `D_x` と `D_y` を使用して、テンソル積構造に基づく長方形上の 2D [`TensorProductOperator`](@ref) を作成します。演算子 `D_x` は x 方向で、`D_y` は y 方向で使用されます。

構築については、以下も参照してください：

  * Sigrun Ortleb (2021) 数値流体力学のための数値手法：高次 SBP スキーム、IMEX 伝達-拡散分割および生産-破壊-PDE のための正の保持、カッセル大学の habilitation 論文、[DOI: 10.17170/kobra-202301037274](https://doi.org/10.17170/kobra-202301037274)、第 1.2.4 章。
  * Magnus Svärd, Jan Nordström (2014) 初期境界値問題のための部分和スキームのレビュー、計算物理学ジャーナル 268, pp. 17-38、[DOI: 10.1016/j.jcp.2014.02.031](https://doi.org/10.1016/j.jcp.2014.02.031)。
