`DynamicPPL`、すなわち `Turing` のバックエンドを使用して、対数密度を構築します。

Pigeons を使用するには、`DynamicPPL` または `Turing` を現在のセッションにインポートする必要があります。

  * `model`: `DynamicPPL.Model`。
  * `context`: 完全な結合を評価するための `DynamicPPL.DefaultContext` または、事前分布のみを評価するための `DynamicPPL.PriorContext`。
  * `dimension`: `model` からの単一のランダムサンプルで観測されたスカラー値の総数。これは、静的計算グラフを持つモデルで勾配ベースのサンプラーが探索者として使用されるときに、`LogDensityProblems` および `LogDensityProblemsAD` インターフェースによって使用されます。

    !!! warning
        動的計算グラフを持つモデルを対象とする探索者は、このフィールドの値に依存すべきではありません。
