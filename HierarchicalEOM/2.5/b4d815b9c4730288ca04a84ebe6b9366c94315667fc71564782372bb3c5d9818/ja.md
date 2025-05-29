```
expect(op, ados; take_real=true)
```

与えられた `ados` の縮退密度演算子に対する演算子 `op` の期待値を返します。すなわち、

$$
\textrm{Tr}\left[ O \rho \right],
$$

ここで $O$ は演算子であり、$\rho$ は与えられた ADOs における縮退密度演算子です。

# パラメータ

  * `op` : 期待値を取る演算子 $O$
  * `ados::ADOs` : HEOM モデルのための補助密度演算子
  * `take_real::Bool` : トレースの実部を自動的に取るかどうか。デフォルトは `true`

# 戻り値

  * `exp_val` : 期待値
