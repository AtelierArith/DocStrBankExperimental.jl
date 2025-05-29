```
g = Geometry([;kwargs...])
```

CloudSeisデータセットに関連付けられたジオメトリオブジェクトを返します。これには、原点（`o`）と3つの直交ベクトル（`u`、`v`、`w`）が含まれます。さらに、TTI地球モデルの方位がどのように定義されるかを指定するために、正の方位の特定の方向と、それが測定される軸を指定することができます。これは、3次元空間におけるモデルの向きを説明する際に便利です。

# キーワード引数

  * `ox=0,oy=0,oz=0` グリッド原点
  * `ux=0,uy=0,uz=1` uベクトルで、u軸の端が点(ox+ux,oy+uy,oz+uz)にある
  * `vx=0,vy=0,vz=1` vベクトルで、u軸の端が点(ox+vx,oy+vy,oz+vz)にある
  * `wx=0,wy=0,wz=1` wベクトルで、u軸の端が点(ox+wx,oy+wy,oz+wz)にある
  * `u1=1,un=2` グリッドを説明するために使用できる整数の端点（u軸）（例：有限差分用）
  * `v1=1,vn=2` グリッドを説明するために使用できる整数の端点（v軸）（例：有限差分用）
  * `w1=1,wn=2` グリッドを説明するために使用できる整数の端点（w軸）（例：有限差分用）
  * `umin=0.0,umax=1.0` モデルに使用されるジオメトリの部分（u軸）
  * `vmin=0.0,vmax=1.0` モデルに使用されるジオメトリの部分（v軸）
  * `wmin=0.0,wmax=1.0` モデルに使用されるジオメトリの部分（w軸）
  * `x_direction="east"` 'x'が平行なコンパス方向
  * `y_direction="north"` 'y'が平行なコンパス方向
  * `z_direction="depth"` 'z'が平行なコンパス方向
  * `tti_angle_units="degrees"` TTIモデルのために、傾きと方位角が（"degrees"、"radians"、または"unknown"）で保存されるかどうかを指定
  * `tti_azimuth_positive_direction="counter clockwise"` TTIモデルのために、方位の向きを定義（"clockwise"、"counter clockwise"または"unknown"）
  * `tti_azimuth_origin_axis="v"` TTIモデルのために、方位が測定される軸と方位が0である軸を定義（"u"、"v"、"w"、"x"、"y"、"-u"、"-v"、"-w"、"-x"、"-y"または"unknown"から選択）
  * `tti_symmetry_axis_z_direction="elevation"` TTIモデルのために、対称軸の法線のz = (0,0,1)への投影が上（elevation）または下（depth）を指すかどうかを定義

# 注意事項

  * このメソッドは、u、v、wベクトルが直交しているかどうかを確認しません
  * 方位異方性を必要としないモデル（例：等方性、VTI）の場合、`tti_azimuth_positive_direction`と`tti_azimuth_origin_axis`を"unknown"に設定することが便利です
  * `umin、umax、vmin、vmax、wmin、wmax`は、u、v、wのサブセットまたはスーパーセットがモデル領域を説明する場合に使用されます。たとえば、`(ux,uy,uz)`の大きさが単一のモデルグリッドセルの長さである場合、`umin=0`および`umax=(nu-1)`が適切です。
