```
cocoReg(type, order, data, covariates=nothing, starting_values=nothing, link_function="log", lower_bound_covariates=-Inf, max_loop=nothing, optimizer=Fminbox(LBFGS()))
```

指定されたタイプと順序に基づいて、一般化ポアソンまたはポアソンの尤度を使用してカウント回帰モデルをフィットします。この関数は最適化問題を設定し、初期値とパラメータの境界を決定し、自動微分最適化器を使用して負の対数尤度を最小化します。

# 引数

  * `type`: モデルタイプを示す文字列（"GP"は一般化ポアソン、"Poisson"はポアソン）。
  * `order`: 自己回帰の順序（1または2）。
  * `data`: 観測されたカウントのベクトル。
  * `covariates`（オプション）: 説明変数の値の行列。
  * `starting_values`（オプション）: 最適化器の初期値。
  * `link_function`（オプション）: リンク関数を指定する文字列（デフォルトは`"log"`）。
  * `lower_bound_covariates`（オプション）: 説明変数パラメータの下限（デフォルトは`-Inf`）。
  * `max_loop`（オプション）: 尤度計算における最大反復または切り捨てを制御するパラメータ。
  * `optimizer`（オプション）: 使用する最適化アルゴリズム（デフォルトは`Fminbox(LBFGS())`）。

# 戻り値

次の内容を含む辞書:

  * `"parameter"`: フィットされたパラメータベクトル。
  * `"covariance_matrix"`: パラメータ共分散の推定値としての逆ヘッセ行列。
  * `"log_likelihood"`: 最適点での対数尤度値。
  * モデルの詳細には`type`、`order`、`data`、`covariates`、`link`、初期値、最適化器設定、およびパラメータの境界が含まれます。
  * `"se"`: 推定されたパラメータの標準誤差。
