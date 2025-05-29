```
read_smac1_binary_info(filename::String)
```

`Smac1ImageInfo`構造体の画像情報を返します。

## `Smac1ImageInfo`フィールド

  * `snap::Int32`:             入力スナップショットの数
  * `z::Float32`:              スナップショットの赤方偏移
  * `m_vir::Float32`:          ハローのウィリアル質量
  * `r_vir::Float32`:          ハローのウィリアル半径
  * `xcm::Float32`:            画像中心のx座標
  * `ycm::Float32`:            画像中心のy座標
  * `zcm::Float32`:            画像中心のz座標
  * `z_slice_kpc::Float32`:    画像の深さ（kpc単位）
  * `boxsize_kpc::Float32`:    画像のxyサイズ（kpc単位）
  * `boxsize_pix::Float32`:    画像のxyサイズ（ピクセル単位）
  * `pixsize_kpc::Float32`:    1ピクセルのサイズ（kpc単位）
  * `xlim::Array{Float64,1}`:  画像のx制限
  * `ylim::Array{Float64,1}`:  画像のy制限
  * `zlim::Array{Float64,1}`:  画像のz制限
  * `units::String`:           画像の単位文字列
