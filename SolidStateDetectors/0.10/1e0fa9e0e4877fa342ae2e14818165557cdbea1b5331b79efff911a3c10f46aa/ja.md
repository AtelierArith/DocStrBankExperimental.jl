```
NBodyChargeCloud(center::CartesianPoint{T}, energy::T, particle_type::Type{PT} = Gamma; kwargs...)
```

指定された位置での `energy` 蓄積に対して [`NBodyChargeCloud`](@ref) を返します。この位置は、中心の電荷に囲まれたプラトン固体からなるシェルによって定義される `center` です。

## 引数

  * `center::CartesianPoint{T}`: [`NBodyChargeCloud`](@ref) の中心位置。
  * `energy::RealQuantity`: 単位付きの蓄積エネルギー。単位が指定されていない場合、値は eV の単位で解析されます。
  * `particle_type`: エネルギーを蓄積した粒子の [`ParticleType`](@ref)。デフォルトは `Gamma` です。

## キーワード

  * `radius::T`: [`NBodyChargeCloud`](@ref) の半径の推定値。デフォルトは `radius_guess` を介して `particle_type` から決定されます。
  * `number_of_shells::Int`: `center` 点の周りのシェルの数。デフォルトは `2` です。
  * `shell_structure`: シェル内で電荷が分布する幾何学。デフォルトは `Dodecahedron` です。

## 例

```julia
center = CartesianPoint{T}([0,0,0])
energy = 1460u"keV"
NBodyChargeCloud(center, energy, number_of_shells = 3, shell_structure = SolidStateDetectors.Icosahedron)
```

!!! note
    `energy` に単位付きの値を使用するには、パッケージ [Unitful.jl](https://github.com/PainterQubits/Unitful.jl) が必要です。

