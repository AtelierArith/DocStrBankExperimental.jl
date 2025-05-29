```
test_fit_simrna(; rtarget, transitions, G, nRNA, nalleles, fittedparam, fixedeffects, rinit, totalsteps, nchains)
```

提供されたパラメータを使用してシミュレートされたRNAヒストグラムをフィットさせ、ターゲットと比較します。

# 引数

  * `rtarget`: ターゲットレートパラメータ。
  * `transitions`, `G`, `nRNA`, `nalleles`: モデル構造とカウント。
  * `fittedparam`, `fixedeffects`, `rinit`: フィッティングオプション。
  * `totalsteps`: シミュレーションステップの数。
  * `nchains`: MCMCチェーンの数。

# 戻り値

  * (フィットしたレート, ターゲットレート) のタプル。
