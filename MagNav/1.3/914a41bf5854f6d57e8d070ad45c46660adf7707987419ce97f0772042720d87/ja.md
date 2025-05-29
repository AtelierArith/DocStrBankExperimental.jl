```
create_TL_A(flux::MagV, ind = trues(length(flux.x));
            Bt       = sqrt.(flux.x.^2+flux.y.^2+flux.z.^2)[ind],
            terms    = [:permanent,:induced,:eddy],
            Bt_scale = 50000,
            return_B = false)
```

トレス-ローソン `A` 行列をベクトル磁力計測定を使用して作成します。オプションで、全体のフィールドの大きさと導関数を返します。

**引数:**

  * `flux`:     `MagV` ベクトル磁力計測定構造体
  * `ind`:      （オプション）選択されたデータインデックス
  * `Bt`:       （オプション）ベクトル磁力計測定または修正トレス-ローソンのスカラー磁力計測定の大きさ [nT]
  * `terms`:    （オプション）使用するトレス-ローソン項 {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `Bt_scale`: （オプション）誘導および渦電流項のスケーリング係数 [nT]
  * `return_B`: （オプション）trueの場合、`Bt` および `B_dot` も返す

**返り値:**

  * `A`:     トレス-ローソン `A` 行列
  * `Bt`:    `return_B = true` の場合、全体のフィールド測定の大きさ [nT]
  * `B_dot`: `return_B = true` の場合、全体のフィールドベクトルの有限差分 [nT]
