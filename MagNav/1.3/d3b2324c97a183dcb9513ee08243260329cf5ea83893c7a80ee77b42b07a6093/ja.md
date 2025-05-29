```
plsr_fit(x, y, k::Int = size(x,2), no_norm = falses(size(x,2));
         data_norms::Tuple = (zeros(1,1),zeros(1,1),[0.0],[0.0]),
         l_segs::Vector    = [length(y)],
         return_set::Bool  = false,
         silent::Bool      = false)
```

指定された出力次元を持つデータに対して、マルチ入力・マルチ出力（MIMO）部分最小二乗回帰（PLSR）モデルをフィットします。PLSRは、成分の数が正則化の強さを制御する正則化線形回帰の一種です。

**引数:**

  * `x`:          `N` x `Nf` データ行列（`Nf`は特徴の数）
  * `y`:          長さ`N`のターゲットベクトル
  * `k`:          （オプション）成分の数
  * `no_norm`:    （オプション）正規化しない特徴の長さ`Nf`のブールインデックス
  * `data_norms`: （オプション）データ正規化の長さ`4`のタプル、`(x_bias,x_scale,y_bias,y_scale)`
  * `l_segs`:     （オプション）`lines`の長さの長さ`N_lines`のベクトル、sum(l_segs) = `N`
  * `return_set`: （オプション）trueの場合、他の出力の代わりに`coef_set`を返す
  * `silent`:     （オプション）trueの場合、出力を表示しない

**戻り値:**

  * `model`:      PLSRベースのモデルの長さ`2`のタプル（長さ`Nf`の係数、バイアス=`0`）
  * `data_norms`: データ正規化の長さ`4`のタプル、`(x_bias,x_scale,y_bias,y_scale)`
  * `y_hat`:      長さ`N`の予測ベクトル
  * `err`:        長さ`N`の平均補正（行ごと）の誤差
  * `coef_set`:   `return_set = true`の場合、係数のセット（サイズ `Nf` x `Ny` x `k`）
