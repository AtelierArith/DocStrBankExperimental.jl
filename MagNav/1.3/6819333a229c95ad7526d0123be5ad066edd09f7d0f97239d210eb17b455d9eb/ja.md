```
create_TL_coef(flux::MagV, B, ind = trues(length(flux.x));
               Bt         = sqrt.(flux.x.^2+flux.y.^2+flux.z.^2)[ind],
               λ          = 0,
               terms      = [:permanent,:induced,:eddy],
               pass1      = 0.1,
               pass2      = 0.9,
               fs         = 10.0,
               pole::Int  = 4,
               trim::Int  = 20,
               Bt_scale   = 50000,
               return_var = false)
```

ベクトルおよびスカラーの磁力計測定を使用して、バンドパス、ローパス、またはハイパスフィルタを用いてトレス・ローソン係数を作成します。

**引数:**

  * `flux`:       `MagV` ベクトル磁力計測定構造体
  * `B`:          スカラー磁力計測定 [nT]
  * `ind`:        （オプション）選択されたデータインデックス
  * `Bt`:         （オプション）修正トレス・ローソンのためのベクトル磁力計測定またはスカラー磁力計測定の大きさ [nT]
  * `λ`:          （オプション）リッジパラメータ
  * `terms`:      （オプション）使用するトレス・ローソン項 {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `pass1`:      （オプション）第一パスバンド周波数 [Hz]
  * `pass2`:      （オプション）第二パスバンド周波数 [Hz]
  * `fs`:         （オプション）サンプリング周波数 [Hz]
  * `pole`:       （オプション）バターワースフィルタの極数
  * `trim`:       （オプション）フィルタリング後にトリムする要素の数
  * `Bt_scale`:   （オプション）誘導および渦電流項のスケーリングファクター [nT]
  * `return_var`: （オプション）trueの場合、`B_var`も返す

**戻り値:**

  * `coef`:  トレス・ローソン係数
  * `B_var`: `return_var = true`の場合、フィット誤差分散
