```julia
abstract type OneParameterLogisticModel <: ItemResponseFunctions.DichotomousItemResponseModel
```

1パラメータロジスティックモデルの抽象表現で、アイテム応答関数は次のように与えられます。

$$
P(Y_{ij}=1|\theta_i,\boldsymbol{\beta}_j) = \mathrm{logistic}(\theta_i - b_j)
$$

アイテムパラメータ `beta` は、数値または次のフィールドを持つ分解可能なオブジェクトとして渡すことができます。

  * `b`: アイテムの難易度（位置）

**エイリアス:** `OnePL`
