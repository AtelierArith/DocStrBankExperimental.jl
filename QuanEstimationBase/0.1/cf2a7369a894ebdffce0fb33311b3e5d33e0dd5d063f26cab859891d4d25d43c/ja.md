```
offline(apt::Adapt_MZI, alg; target::Symbol=:sharpness, eps = GLOBAL_EPS, seed=1234)
```

MZIにおけるオフライン適応位相推定。

  * `apt`: `x`、`p`、および `rho0` を含む適応MZI構造体。
  * `alg`: 最適な調整可能位相を検索するためのアルゴリズム。ここでは、DEとPSOが利用可能。
  * `target`: 調整可能位相を計算するためのターゲット関数を設定します。オプションは「sharpness」と「MI」です。
  * `eps`: マシンエプシロン。
  * `seed`: ランダムシード。
