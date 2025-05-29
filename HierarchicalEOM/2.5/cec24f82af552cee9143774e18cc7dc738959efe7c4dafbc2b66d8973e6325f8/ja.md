```
expect(op, ados_list; take_real=true)
```

演算子 `op` の期待値のリストを返します。これは、与えられた `ados_list` の縮退密度演算子に対応します。すなわち、

$$
\textrm{Tr}\left[ O \rho \right],
$$

ここで $O$ は演算子であり、$\rho$ は `ados_list` のいずれかの `ADO` における縮退密度演算子です。

# パラメータ

  * `op` : 期待値を取る演算子 $O$
  * `ados_list::Vector{ADOs}` : HEOM モデルのための補助密度演算子のリスト
  * `take_real::Bool` : トレースの実部を自動的に取るかどうか。デフォルトは `true`

# 戻り値

  * `exp_val` : 期待値
