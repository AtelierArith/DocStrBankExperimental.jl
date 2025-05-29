不等式測定の構造体を作成します。これは主に世界銀行の本の第5章と第6章から取られています。

1. `rawdata` 重みと収入を含む列のある行列
2. `atkinson_es` アトキンソン指数の不平等回避値
3. `generalised_entropy_alphas`
4. `weightpos` - 重みの列
5. `incomepos` - 収入の列

返されるのは、不平等測定の辞書で、以下を含みます：

  * `Gini`;
  * `Atkinson`、`atkinson_es`の各値について;
  * `Theil`;
  * `generalised_entropy`;
  * `Hoover`;
  * `Theil`;
  * `Palma`.

世界銀行の第5章と第6章、及びコブハムとサムナーによるパルマについても参照してください。

構造体には以下も含まれます：

  * `total_income`
  * `total_population`
  * `average_income`
  * `deciles`.
