`CoinTest(pvalue::Float64,testnumber::Int)`

テストコイン関数。

# 引数

  * `pvalue`:真の出力の確率（0より大きく1未満）。小数点以下1桁または2桁の値を入力してください。
  * `testnumber`:テスト番号。

# 戻り値

  * `Bool`:真の頻度は理論的にpvalueに近い。

# 例

using BipartiteNull;

CoinTest(0.5,100000)
