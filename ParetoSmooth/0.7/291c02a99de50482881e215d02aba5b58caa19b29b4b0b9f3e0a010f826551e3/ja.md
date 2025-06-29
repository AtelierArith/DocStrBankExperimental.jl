```
ModelComparison
```

モデル比較の結果を含む構造体です。

# フィールド

  * `pointwise::KeyedArray`: ポイントワイズ推定の `KeyedArray`。[`PsisLoo`]@ref を参照してください。

      * `estimates::KeyedArray`: モデル比較の結果を含むテーブルで、以下の列があります –

          * `cv_elpd`: モデル間の総留出交差検証スコアの差。
          * `cv_avg`: モデル間の平均LOO-CVスコアの差。
          * `weight`: 各モデルに割り当てられたAkaike風の重みのセットで、擬似ベイズモデル平均に使用できます。
      * `std_err::NamedTuple`: `cv_elpd`の標準誤差を含む名前付きタプル。これらの推定量は、実際には substantial overlap があるにもかかわらず、すべてのフォールドが独立であると（誤って）仮定しているため、下方バイアスのある推定量を生成します。LOO-CVの差は*漸近的に正規分布*ではないため、これらの標準誤差を使用して信頼区間を計算することはできません。
      * `gmpd::NamedTuple`: 予測分布の幾何平均。これは、モデルによって各データポイントに割り当てられた確率の幾何平均、すなわち `exp(cv_avg)` に等しいです。この指標は分類器（離散的な結果を持つ変数）に対してのみ意味があります。モデルがどれだけ正確であったかを測るものと考えることができます：常に誤って予測するモデルはGMPDが0になり、常に正しく予測するモデルはGMPDが1になります。ただし、GMPDはモデルが実際に起こった結果に対して0または1以外の確率を割り当てるときに、0と1の間で「部分ポイント」を与えます。

参照：[`PsisLoo`](@ref)
