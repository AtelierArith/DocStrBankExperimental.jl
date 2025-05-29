```
voxel_grav(X::Array{Float64, 3}, Y::Array{Float64, 3}, Z::Array{Float64, 3}, RHO::Array{Float64, 3};
refMod="AVG", lengthUnit="m", rhoTol=1e-9, Topo=[], outName="Bouguer", printing=true)
```

ブーゲル異常と勾配を計算します

# 必要な引数:

  * `X`,`Y`,`Z`:       グリッドの座標を持つ3D行列（Xは最初の次元で変化し、Yは2番目、Z（垂直）は3番目）
  * `RHO`:         各グリッド点での密度を持つ3D行列 [kg/m^3]

# オプションの引数:

  * `refMod`:      各深さの参照密度を持つ1Dベクトル。代わりに、文字列 "NE", "SE", "SW", "NW", "AVG" を使用できます。その場合、`RHO` の隅の1つが参照モデルとして使用されます。"AVG" の場合、参照モデルは各深さスライスの平均です。
  * `lengthUnit`:  座標と地形ファイルの単位。"m" または "km"
  * `rhoTol`:      `rhoTol` より小さい密度差は無視されます [kg/m^3]
  * `Topo`:        表面の地形を持つ2D行列（paraview出力にのみ関連）
  * `outName`:     paraview出力の名前（ファイルタイプを含めないでください）
  * `printing`:    追加情報の印刷を有効にする [`true` または `false`]
