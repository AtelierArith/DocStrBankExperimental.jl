```
NearSourceSaturationParameters
```

近接ソース飽和パラメータの構造体。`GeometricSpreadingParameters` 構造体の構造を模倣しています。フィールドを保持します：

  * `mRefi` 参照マグニチュード
  * `hconi` 制約付き係数、AD目的で自由ではありません
  * `hvari` 変数係数、AD目的で自由です
  * `hfree` 定数または変数のパラメータを示す `Bool` インスタンスのベクター、または `BitVector`
  * `exponent` 同等の点ソース距離計算に使用される指数： $r_{ps} = \left[r_{rup}^n + h(m)^n\right]^{1/n}$
  * `model` 飽和モデルのタイプを定義するシンボル：

      * `:BT15` Boore & Thompson (2015)
      * `:YA15` Yenier & Atkinson (2015)
      * `:CY14` 平均 Chiou & Youngs (2014)
      * `:None` ゼロ飽和長を返します
      * `:ConstantConstrained` AD操作の対象とならない固定飽和長
      * `:ConstantVariable` AD操作の対象となる固定飽和長（すなわち、`<:Dual` です）
