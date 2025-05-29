```julia
abstract type RatingScaleModel <: ItemResponseFunctions.PolytomousItemResponseModel
```

アイテムカテゴリ応答関数によって与えられる評価スケールモデルを表す抽象型

$$
P(Y_{ij} = y,| \theta_i, \boldsymbol{\beta}_j) =     \frac{\exp \sum_{s=1}^y (\theta_i - b_j + t_{s})}     {1 + \sum_{k=1}^{K_j} \exp \sum_{s=1}^k (\theta_i - b_j + t_{s})}
$$

アイテムパラメータ `beta` は、以下のフィールドを持つ解体可能なオブジェクトでなければなりません：

  * `b`: アイテムの難易度（位置）
  * `t`: 閾値パラメータのベクトル

**エイリアス:** `RSM`
