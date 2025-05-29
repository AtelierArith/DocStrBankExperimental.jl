```julia
abstract type ThreeParameterLogisticModel <: ItemResponseFunctions.DichotomousItemResponseModel
```

3パラメータロジスティックモデルの抽象表現で、アイテム応答関数は次のように与えられます。

$$
P(Y_{ij}=1|\theta_i,\boldsymbol{\beta}_j) = c_j + (1 - c_j)\cdot\mathrm{logistic}(a_j(\theta_i - b_j))
$$

アイテムパラメータ `beta` は、以下のフィールドを持つ解体可能なオブジェクトでなければなりません。

  * `a`: アイテムの識別力
  * `b`: アイテムの難易度（位置）
  * `c`: 下限漸近線

**エイリアス:** `ThreePL`
