```
krr_fit(x, y, no_norm = falses(size(x,2));
        k::Kernel           = PolynomialKernel(;degree=1),
        λ::Real             = 0.5,
        norm_type_x::Symbol = :standardize,
        norm_type_y::Symbol = :standardize,
        data_norms::Tuple   = (zeros(1,1),zeros(1,1),[0.0],[0.0]),
        l_segs::Vector      = [length(y)],
        silent::Bool        = false)
```

カーネルリッジ回帰（KRR）モデルをデータにフィットさせます。

**引数:**

  * `x`:           `N` x `Nf` データ行列（`Nf` は特徴量の数）
  * `y`:           長さ`N` のターゲットベクトル
  * `no_norm`:     （オプション）正規化しない特徴量の長さ`Nf` のブールインデックス
  * `k`:           （オプション）カーネル
  * `λ`:           （オプション）リッジパラメータ
  * `norm_type_x`: （オプション）`x` データ行列の正規化
  * `norm_type_y`: （オプション）`y` ターゲットベクトルの正規化
  * `data_norms`:  （オプション）データの正規化の長さ`4` のタプル、`(x_bias,x_scale,y_bias,y_scale)`
  * `l_segs`:      （オプション）`lines` の長さの長さ`N_lines` のベクトル、sum(l_segs) = `N`
  * `silent`:      （オプション）true の場合、出力なし

**戻り値:**

  * `model`:      KRRベースのモデルの長さ`3` のタプル、(`k`, 長さ`N` の係数, `N` x `Nf` データ行列, 正規化済み)
  * `data_norms`: 長さ`4` のデータ正規化のタプル、`(x_bias,x_scale,y_bias,y_scale)`
  * `y_hat`:      長さ`N` の予測ベクトル
  * `err`:        長さ`N` の平均補正（行ごと）の誤差
