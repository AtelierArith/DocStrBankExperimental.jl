`Coin(pvalue::Float64)`

確率によって真を出力します

# 引数

  * `pvalue`: 真の出力の確率（0より大きく1未満）。小数点以下1桁または2桁の値を入力してください。

# 戻り値

  * `Bool`: 2つの値、真または偽。

# 例

using BipartiteNull;

Coin(0.5)
