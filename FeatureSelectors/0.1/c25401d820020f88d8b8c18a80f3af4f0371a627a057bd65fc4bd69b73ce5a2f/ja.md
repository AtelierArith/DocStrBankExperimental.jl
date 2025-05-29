`UnivariateFeatureSelector` には以下のフィールドがあります：

  * `method::Function` (必須) - 特徴の重要性を計算するためのメソッド。選択したメソッドがスコアリングを決定します。以下は、利用可能な統計的手法を用いたスコアリングです。

      * 相関 - スコアが高いほど重要度が高い

          * `pearson_correlation`
      * P値 - スコアが低いほど重要度が高い

          * `f_test`
          * `chisq_test`
  * `k::Union{Int64,Nothing}` - 対象変数に対する相関が最も高い上位 `k` 特徴を選択します。これを無視するには、k == nothing を指定します。デフォルトは nothing です。
  * `threshold::Union{Float64,Nothing}` - 相関が閾値以上の特徴を選択します。無視するには、単に threshold を nothing に設定します（デフォルトの動作）。
