```
dc3d(x::T, y::T, z::T, α::T, dep::T, dip::T,
    al::Union{A, SubArray}, aw::Union{A, SubArray}, disl::A
    ) where {T <: Number, A <: AbstractVecOrMat{T}}
```

弾性等方性半空間における長方形のひずみ源による変位と変位の勾配を計算します。

詳細については [dc3d](http://www.bosai.go.jp/study/application/dc3d/DC3Dhtml_E.html) を参照してください。また、この断層座標系はこのパッケージで広く使用されています。

## 引数

  * `x`, `y`, `z`: 観測位置、$z ≤ 0$ の範囲
  * `α`: 弾性定数
  * `dep`: 断層起源の深さ
  * `dip`: 傾斜角（度）
  * `al`: ストライク方向（x軸）に沿った2つの数値を示すベクトル
  * `aw`: ダウンドリップ方向（y-z平面）に沿った2つの数値を示すベクトル
  * `disl`: ストライク方向、ダウンドリップ方向、引張方向のそれぞれのひずみを示す3つの数値を含むベクトル

## 出力

12個の数値からなるベクトルで、各要素は $u_{x}$, $u_{y}$, $u_{z}$, $u_{x,x}$, $u_{y,x}$, $u_{z,x}$, $u_{x,y}$, $u_{y,y}$, $u_{z,y}$, $u_{x,z}$, $u_{y,z}$, $u_{z,z}$ です。
