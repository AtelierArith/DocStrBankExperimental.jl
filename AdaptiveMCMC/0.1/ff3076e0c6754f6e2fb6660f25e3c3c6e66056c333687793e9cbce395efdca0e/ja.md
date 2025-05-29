adapt_rb!(s, r, α)

アンドリュー & トムズによって提案された適応メトロポリスのラオ-ブラックウェル化適応ステップ (Statist. Comput. 2008)。

# 引数:

  * `s`: AdaptiveMetropolis オブジェクト
  * `r`: RWMState オブジェクト
  * `α`: 受け入れ率

注: この関数は accept!(r) を呼び出す *前に* 呼び出す必要があります。
