```
calc_spcorr_mtx(vecs::AbstractMatrix{<:Number}, window)
calc_spcorr_mtx(vecs::AbstractMatrix{<:Number}, vals::AbstractVector{<:Number}, window)
```

観測のセットに対するペアワイズスペクトル（ピアソン）相関を計算します。

引数:

  * vecs: 行に観測/特徴、列にスペクトル成分を持つ左または右の特異ベクトルのセット
  * vals: 特異値のベクトル
  * window: 相関を計算するための`vecs`列のインデックスのセット

戻り値:

  * 各ピクセルが観測のペア間の相関である相関行列
