```
TL_mat2vec(TL_coef_p, TL_coef_i, TL_coef_e, terms; Bt_scale = 50000f0)
```

トレス-ローソン係数の行列形式からベクトル形式を抽出します。

**引数:**

  * `TL_coef_p`: 永続的場係数の長さ`3`のベクトル
  * `TL_coef_i`: 誘導場係数の`3` x `3` 対称行列、正規化されていない
  * `TL_coef_e`: 渦電流係数の`3` x `3` 行列、正規化されていない
  * `terms`:     使用されるトレス-ローソン項 {`:permanent`,`:induced`,`:eddy`}
  * `Bt_scale`:  (オプション) 誘導および渦電流項のスケーリングファクター [nT]

**戻り値:**

  * `TL_coef`: トレス-ローソン係数
