```
linear_test(x_norm, y, y_bias, y_scale, model::Tuple;
            l_segs::Vector = [length(y)],
            silent::Bool   = false)
```

線形モデルの性能を評価します。

**引数:**

  * `x_norm`:  `N` x `Nf` 正規化データ行列（`Nf`は特徴量の数）
  * `y`:       長さ`N`のターゲットベクトル
  * `y_bias`:  `y`ターゲットベクトルのバイアス（平均、最小、またはゼロ）
  * `y_scale`: `y`ターゲットベクトルのバイアススケーリング係数（標準偏差、最大-最小、または1）
  * `model`:   長さ`2`のタプルのモデル（長さ`Nf`の係数、バイアス）
  * `l_segs`:  （オプション）長さ`N_lines`のベクトルの長さ`lines`、sum(l_segs) = `N`
  * `silent`:  （オプション）trueの場合、出力なし

**戻り値:**

  * `y_hat`: 長さ`N`の予測ベクトル
  * `err`:   長さ`N`の平均補正（行ごと）の誤差
