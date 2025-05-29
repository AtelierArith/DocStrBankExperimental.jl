```
TL_vec2mat(TL_coef::Vector, terms; Bt_scale = 50000f0)
```

ベクトル形式からトレス-ローソン係数の行列形式を抽出します。

**引数:**

  * `TL_coef`:  トレス-ローソン係数（`:permanent` と `:induced` を含む必要があります）
  * `terms`:    使用されるトレス-ローソン項 {`:permanent`,`:induced`,`:eddy`}
  * `Bt_scale`: （オプション）誘導および渦電流項のスケーリングファクター [nT]

**戻り値:**

  * `TL_coef_p`: 長さ`3`の永久場係数のベクトル
  * `TL_coef_i`: `3` x `3` の対称行列の誘導場係数、正規化解除済み
  * `TL_coef_e`: `3` x `3` の渦電流係数の行列、正規化解除済み
