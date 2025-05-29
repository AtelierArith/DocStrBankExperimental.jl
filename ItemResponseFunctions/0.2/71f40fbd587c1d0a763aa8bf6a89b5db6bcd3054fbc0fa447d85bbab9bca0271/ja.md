```julia
abstract type PartialCreditModel <: ItemResponseFunctions.PolytomousItemResponseModel
```

部分クレジットモデルを表す抽象型で、アイテムカテゴリ応答関数は次のように与えられます。

$$
P(Y_{ij} = y,| \theta_i, \boldsymbol{\beta}_j) =     \frac{\exp \sum_{s=1}^y (\theta_i - b_j + t_{js})}     {1 + \sum_{k=1}^{K_j} \exp \sum_{s=1}^k (\theta_i - b_j + t_{js})}
$$

アイテムパラメータ `beta` は、次のフィールドを持つ解体可能なオブジェクトでなければなりません：

  * `b`: アイテムの難易度（位置）
  * `t`: 閾値パラメータのベクトル

**エイリアス:** `PCM`
