```julia
abstract type FiveParameterLogisticModel <: ItemResponseFunctions.DichotomousItemResponseModel
```

5パラメータロジスティックモデルの抽象表現で、アイテム応答関数は次のように与えられます。

$$
P(Y_{ij}=1|\theta_i,\boldsymbol{\beta}_j) = c_j + (d_j - c_j)\cdot\mathrm{logistic}(a_j(\theta_i - b_j))^{e_j}
$$

アイテムパラメータ `beta` は、次のフィールドを持つ解体可能なオブジェクトでなければなりません。

  * `a`: アイテムの識別力
  * `b`: アイテムの難易度（位置）
  * `c`: 下限漸近線
  * `d`: 上限漸近線
  * `e`: アイテムの硬さ

**エイリアス:** `FivePL`
