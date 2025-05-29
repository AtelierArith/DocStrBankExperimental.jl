```
divmat(MR::Type{DeforModelRed3D}, N::AbstractMatrix{T}, gradN::AbstractMatrix{T}, c::AbstractMatrix{T})
```

三次元多様体要素の変位発散行列を計算します。

# 引数

  * `N` = 基底関数の値の行列
  * `gradN` = 材料の方向における直交座標に対する基底関数の勾配の行列
  * `c` = グローバル直交座標系における評価点の空間座標の配列。
  * `Rm` = ローカル材料方向座標系の単位基底ベクトルを列として持つ直交行列。`size(Rm)= (ndim,mdim)`、ここで `ndim` = 埋め込み空間の空間次元の数（ここでは `ndim == 3`）、`mdim` = 多様体の次元の数（ここでは `mdim == 3`）。

# 出力

  * `divmat` = 変位発散行列、ここで `size(divmat) = (1,nnodes*dim)`; ここで `dim` = 埋め込み空間の空間次元の数、`nnodes` = 要素上の有限要素ノードの数。行列はバッファとして渡され、ゼロに設定され、非ゼロ成分で埋められます。また、便利のために返されます。
