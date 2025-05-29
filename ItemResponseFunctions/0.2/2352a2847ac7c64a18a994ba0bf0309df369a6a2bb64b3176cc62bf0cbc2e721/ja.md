```julia
abstract type OneParameterLogisticPlusGuessingModel <: ItemResponseFunctions.DichotomousItemResponseModel
```

1パラメータロジスティック + 推測モデルの抽象表現で、アイテム応答関数は次のように与えられます。

$$
P(Y_{ij}=1|\theta_i,\boldsymbol{\beta}_j) = c + (1 - c) \cdot \mathrm{logistic}(\theta_i - b_j)
$$

アイテムパラメータ `beta` は、次のフィールドを持つ解体可能なオブジェクトでなければなりません。

  * `b`: アイテムの難易度（位置）
  * `c`: 下限漸近線

**エイリアス:** `OnePLG`
