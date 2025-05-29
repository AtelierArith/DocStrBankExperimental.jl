```
cocoPredictKsteps(cocoReg_fit, k, number_simulations=500, covariates=nothing, link="log", matrix_fill=zeros(Int64(number_simulations), Int64(k)))
```

モデルを複数回シミュレーションすることによって、kステップ先の予測分布を生成します。

# 引数

  * `cocoReg_fit`: フィッティングされたモデルの詳細を含む辞書。
  * `k`: 予測するステップ数。
  * `number_simulations` (オプション): 予測分布を生成するためのシミュレーション実行回数 (デフォルトは500)。
  * `covariates` (オプション): シミュレーションで使用するオプションの共変量データ。
  * `link` (オプション): リンク関数を指定する文字列 (デフォルトは `"log"` )。
  * `matrix_fill` (オプション): シミュレーション結果を格納するための事前割り当てされた行列 (デフォルトは `number_simulations` x `k` のゼロ行列)。

# 戻り値

各キー `"prediction_i"` がステップ `i` のカウント値とその相対頻度のデータフレームを含む辞書。また、予測ステップ数を示すキー `"length"` も含まれています。
