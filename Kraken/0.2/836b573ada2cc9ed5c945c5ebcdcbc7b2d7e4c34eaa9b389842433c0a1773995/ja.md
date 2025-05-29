```
kraken(env::Env, freq=15.0; n_modes=5, range_max=5e3, c_low=0.0, c_high=nothing)
```

KRAKENを呼び出して、水中環境における音波の伝播を計算します。

必要な引数:

  * `env`: 水中環境

オプションのキーワード:

  * `freq`: 周波数 (デフォルト: 15)
  * `n_modes`: モードの数 (デフォルト: 5)
  * `range_max`: 最大範囲 (デフォルト: 5e3)
  * `c_low`: 最小音速 (デフォルト: 0)
  * `c_high`: 最大音速 (デフォルト: SSPとSSPHSの最大値)
