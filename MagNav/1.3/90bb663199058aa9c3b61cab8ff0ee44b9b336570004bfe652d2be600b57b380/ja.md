```
krr_test(x, y, data_norms::Tuple, model::Tuple;
         l_segs::Vector = [length(y)],
         silent::Bool   = false)
```

カーネルリッジ回帰（KRR）モデルの性能を評価します。

**引数:**

  * `x`:          `N` x `Nf` データ行列（`Nf` は特徴量の数）
  * `y`:          長さ`N` のターゲットベクトル
  * `data_norms`: 長さ`4` のデータ正規化のタプル、`(x_bias,x_scale,y_bias,y_scale)`
  * `model`:      長さ`3` のKRRベースのモデルのタプル、(`k`, 長さ`N_train` の係数, `N_train` x `Nf` のトレーニングデータ行列、正規化済み)
  * `l_segs`:     （オプション）長さ`N_lines` のベクトル、`lines` の長さ、sum(l_segs) = `N`
  * `silent`:     （オプション）true の場合、出力なし

**戻り値:**

  * `y_hat`: 長さ`N` の予測ベクトル
  * `err`:   長さ`N` の平均補正（行ごと）の誤差
