```
DipoleEmitter3D(x::Real, y::Real, z::Real, photons::Real,
                dx::Real, dy::Real, dz::Real)
```

指定された位置、光子の数、および双極子の向きを持つ `DipoleEmitter3D` を作成します。双極子の向きベクトルは正規化されます。

# 引数

  * `x::Real`: マイクロメートル単位のx座標
  * `y::Real`: マイクロメートル単位のy座標
  * `z::Real`: マイクロメートル単位のz座標
  * `photons::Real`: 光子の数
  * `dx::Real`: 双極子の向きのx成分（正規化済み）
  * `dy::Real`: 双極子の向きのy成分（正規化済み）
  * `dz::Real`: 双極子の向きのz成分（正規化済み）
