```
linear_fit(x, y, no_norm = falses(size(x,2));
           trim::Int           = 0,
           λ::Real             = 0,
           norm_type_x::Symbol = :none,
           norm_type_y::Symbol = :none,
           data_norms::Tuple   = (zeros(1,1),zeros(1,1),[0.0],[0.0]),
           l_segs::Vector      = [length(y)],
           silent::Bool        = false)
```

データに線形回帰モデルをフィットします。

**引数:**

  * `x`:           `N` x `Nf` データ行列（`Nf` は特徴の数）
  * `y`:           長さ-`N` のターゲットベクトル
  * `no_norm`:     （オプション）正規化しない特徴の長さ-`Nf` ブールインデックス
  * `trim`:        （オプション）トリムする要素の数（例：bpfによる）
  * `λ`:           （オプション）リッジパラメータ
  * `norm_type_x`: （オプション）`x` データ行列の正規化
  * `norm_type_y`: （オプション）`y` ターゲットベクトルの正規化
  * `data_norms`:  （オプション）データ正規化の長さ-`4` タプル、`(x_bias,x_scale,y_bias,y_scale)`
  * `l_segs`:      （オプション）`lines` の長さの長さ-`N_lines` ベクトル、sum(l_segs) = `N`
  * `silent`:      （オプション）trueの場合、出力なし

**戻り値:**

  * `model`:      長さ-`2` の線形回帰モデルのタプル、（長さ-`Nf` の係数、バイアス=`0`）
  * `data_norms`: 長さ-`4` のデータ正規化のタプル、`(x_bias,x_scale,y_bias,y_scale)`
  * `y_hat`:      長さ-`N` の予測ベクトル
  * `err`:        長さ-`N` の平均補正（行ごと）の誤差
