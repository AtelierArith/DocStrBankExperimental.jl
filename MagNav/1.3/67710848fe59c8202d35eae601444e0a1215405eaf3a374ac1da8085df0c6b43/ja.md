```
create_TL_A(Bx, By, Bz;
            Bt       = sqrt.(Bx.^2+By.^2+Bz.^2),
            terms    = [:permanent,:induced,:eddy],
            Bt_scale = 50000,
            return_B = false)
```

トレス-ローソン `A` 行列をベクトル磁力計の測定値を使用して作成します。オプションで、全体の磁場の大きさと導関数を返します。

**引数:**

  * `Bx`,`By`,`Bz`: ベクトル磁力計の測定値 [nT]
  * `Bt`:           （オプション）ベクトル磁力計の測定値または修正トレス-ローソンのスカラー磁力計の測定値の大きさ [nT]
  * `terms`:        （オプション）使用するトレス-ローソンの項 {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `Bt_scale`:     （オプション）誘導および渦電流項のスケーリングファクター [nT]
  * `return_B`:     （オプション）trueの場合、`Bt` および `B_dot` も返します

**返り値:**

  * `A`:     トレス-ローソン `A` 行列
  * `Bt`:    `return_B = true` の場合、全体の磁場測定値の大きさ [nT]
  * `B_dot`: `return_B = true` の場合、全体の磁場ベクトルの有限差分 [nT]
