```
rotstressvec!(::Type{DeforModelRed2DStrain},  outstress::Vector{T},  instress::Vector{T},  Rm::_RotationMatrix) where {T}
```

供給された回転行列によって応力ベクトルを回転させます。

回転行列 `Rm` の列によって与えられる「バー」座標系への応力ベクトルの回転を計算します。

  * `outstress` = 出力応力ベクトル、内部で上書きされます
  * `instress` = 入力応力ベクトル
  * `Rm` = 列は「平面」基底ベクトル上の「バー」基底ベクトルの成分です
