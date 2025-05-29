```
linear_test(x, y, data_norms::Tuple, model::Tuple;
            l_segs::Vector = [length(y)],
            silent::Bool   = false)
```

線形モデルの性能を評価します。

**引数:**

  * `x`:          `N` x `Nf` データ行列（`Nf` は特徴量の数）
  * `y`:          長さ`N` のターゲットベクトル
  * `data_norms`: 長さ`4` のデータ正規化のタプル、`(x_bias,x_scale,y_bias,y_scale)`
  * `model`:      長さ`2` のモデルのタプル（長さ`Nf` の係数、バイアス）
  * `l_segs`:     （オプション）長さ`N_lines` の線分の長さのベクトル、`sum(l_segs) = N`
  * `silent`:     （オプション）true の場合、出力なし

**戻り値:**

  * `y_hat`: 長さ`N` の予測ベクトル
  * `err`:   長さ`N` の平均補正（行ごと）の誤差
