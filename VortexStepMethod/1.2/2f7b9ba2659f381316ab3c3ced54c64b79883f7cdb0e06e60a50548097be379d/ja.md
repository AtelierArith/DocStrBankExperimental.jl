```
set_va!(body_aero::BodyAerodynamics, va::VelVector, omega=zeros(MVec3))
```

速度配列を設定し、ウェイクフィラメントを更新します。

# 引数

  * body_aero::BodyAerodynamics: 修正する[BodyAerodynamics](@ref)構造体
  * `va::VelVector`: 見かけの風速の速度ベクトル           [m/s]
  * `omega::VelVector`: x、y、z軸周りの回転率ベクトル            [rad/s]
