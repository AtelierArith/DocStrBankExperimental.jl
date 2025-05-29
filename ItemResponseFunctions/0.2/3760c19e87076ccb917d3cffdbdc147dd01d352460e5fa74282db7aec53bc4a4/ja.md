```julia
abstract type TwoParameterLogisticModel <: ItemResponseFunctions.DichotomousItemResponseModel
```

2パラメータロジスティックモデルの抽象表現で、アイテム応答関数は次のように与えられます。

$$
P(Y_{ij}=1|\theta_i,\boldsymbol{\beta}_j) = \mathrm{logistic}(a_j(\theta_i - b_j))
$$

アイテムパラメータ `beta` は、次のフィールドを持つ解体可能なオブジェクトでなければなりません。

  * `a`: アイテムの識別力
  * `b`: アイテムの難易度（位置）

**エイリアス:** `TwoPL`
