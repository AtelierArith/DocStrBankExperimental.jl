```
CustomError
```

CustomErrorエラーモデル。観測の分散を説明するvariance(::CustomError, p, y)関数の定義と、そのパラメータの初期化関数が必要です。

# 引数

  * `num_params::Int`: エラーファンクションで使用するパラメータの数。
  * `init_f`: パラメータを初期化する関数。デフォルト = init_sigma。
