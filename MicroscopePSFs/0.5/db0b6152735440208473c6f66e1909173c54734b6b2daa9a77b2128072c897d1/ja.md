```
DipoleEmitter3D{T} <: AbstractEmitter
```

位置、向き、光学特性を持つ3Dダイポールエミッタ。

# フィールド

  * `x::T`: マイクロメートル単位のx座標
  * `y::T`: マイクロメートル単位のy座標
  * `z::T`: マイクロメートル単位のz座標
  * `photons::T`: 光子の数
  * `dipole::DipoleVector{T}`: ダイポールの向きベクトル
