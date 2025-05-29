```
blmat!(
    MR::Type{DeforModelRed2DStrain},
    B::AbstractMatrix{T},
    N::AbstractMatrix{T},
    gradN::AbstractMatrix{T},
    c::AbstractMatrix{T},
    Rm::AbstractMatrix{T},
) where {T<:Number}
```

平面ひずみモデルのための二重多様体要素のひずみ-変位行列を計算します。

平面ひずみ設定における二重多様体要素の線形で変位に依存しないひずみ-変位行列を計算します。 *入力変位はグローバルなデカルト座標系であり、出力ひずみは材料座標系で表されます。*

# 引数

  * `N` = 基底関数の値の行列
  * `gradN` = 材料の方向におけるデカルト座標に対する基底関数の勾配の行列
  * `c` = グローバルなデカルト座標における評価点の空間座標の配列
  * `Rm` = ローカル材料方向座標系の単位基底ベクトルを列として持つ直交行列。`size(Rm)= (ndim,mdim)`、ここで `ndim` = 埋め込み空間の空間次元の数（ここでは `ndim <= 3`）、`mdim` = 多様体次元の数（ここでは `mdim == 2`）。

# 出力

  * `B` = ひずみ-変位行列、ここで `size(B) = (nstressstrain,nnodes*dim)`; ここで `nstressstrain`= ひずみの数、`dim` = 埋め込み空間の空間次元の数、`nnodes` = 要素上の有限要素ノードの数。ひずみ成分は `stresscomponentmap` に示されているように順序付けられています。この行列はバッファとして渡され、ゼロに設定され、非ゼロ成分で埋められます。また、便宜のために返されます。
