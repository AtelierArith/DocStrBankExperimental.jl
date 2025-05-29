```
transmittance(m::Material, wavelength::Real, distance::Real; [default::Real=0.0]) -> Real
```

材料の透過率を、指定された波長と距離に対して計算します。

# 引数

  * `m::Material` : 材料オブジェクト
  * `wavelength::Real` : 透過率を計算する波長（単位は $\mu m$）。
  * `distance::Real` : 透過率を計算する距離（単位は $\mu m$）。
  * `default::Real=0.0` : 材料が消失係数に関するデータを含まない場合に返す消失係数のデフォルト値
