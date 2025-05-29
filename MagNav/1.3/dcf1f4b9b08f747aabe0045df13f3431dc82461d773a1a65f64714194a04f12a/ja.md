```
elasticnet_fit(x, y, α::Real = 0.99, no_norm = falses(size(x,2));
               λ::Real           = -1,
               data_norms::Tuple = (zeros(1,1),zeros(1,1),[0.0],[0.0]),
               l_segs::Vector    = [length(y)],
               silent::Bool      = false)
```

データに弾性ネット（リッジ回帰および/またはラッソ）モデルをフィットさせます。

**引数:**

  * `x`:          `N` x `Nf` データ行列（`Nf` は特徴の数）
  * `y`:          長さ`N` のターゲットベクトル
  * `α`:          （オプション）リッジ回帰（`α=0`）対ラッソ（`α=1`）のバランスパラメータ {0:1}
  * `no_norm`:    （オプション）正規化しない特徴の長さ`Nf` のブールインデックス
  * `λ`:          （オプション）弾性ネットパラメータ、`-1` は無視して交差検証で決定
  * `data_norms`: （オプション）データ正規化の長さ`4` のタプル、`(x_bias,x_scale,y_bias,y_scale)`
  * `l_segs`:     （オプション）`lines` の長さの長さ`N_lines` のベクトル、sum(l_segs) = `N`
  * `silent`:     （オプション）true の場合、出力なし

**戻り値:**

  * `model`:      弾性ネットベースのモデルの長さ`2` のタプル（長さ`Nf` の係数、バイアス）
  * `data_norms`: データ正規化の長さ`4` のタプル、`(x_bias,x_scale,y_bias,y_scale)`
  * `y_hat`:      長さ`N` の予測ベクトル
  * `err`:        長さ`N` の平均補正（行ごと）誤差
