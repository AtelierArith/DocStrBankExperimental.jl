```
treeverse(f, gf, s; δ, N, τ=binomial_fit(N,δ), f_inplace=true, logger = TreeverseLog())
```

プログラムメモリを効率的に逆伝播するためのTreeverseアルゴリズム。

位置引数

  * `f`、ステップ関数で、$s_{i+1} = f(s_i)$、
  * `gf`、単一ステップ勾配関数で、$g_i = gf(s_i, g_{i+1})$。$g_{i+1}$が`nothing`の場合、後のステップから渡された勾配を返す必要があります。
  * `s`、初期状態$s_0$、

キーワード引数

  * `δ`、チェックポイントの数、
  * `N`、時間ステップの数、
  * `τ`、スイープの数。デフォルトでは、`binomial(τ+δ, τ) >= N`を満たす最小の整数として選ばれます。
  * `f_inplace = false`、`f`がインプレースかどうか、
  * `logger = TreeverseLog()`、ロガー。

Ref: https://www.tandfonline.com/doi/abs/10.1080/10556789208805505
