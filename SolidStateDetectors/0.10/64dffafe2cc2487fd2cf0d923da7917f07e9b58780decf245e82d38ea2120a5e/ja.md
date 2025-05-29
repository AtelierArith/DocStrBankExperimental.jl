```
NBodyChargeCloud(center::CartesianPoint{T}, energy::T, N::Integer, particle_type::Type{PT} = Gamma; kwargs...)
```

指定された位置での`energy`の沈着に対して[`NBodyChargeCloud`](@ref)を返します。この位置は、中心の電荷に囲まれた約`N`の点電荷が球の表面に均等に分布した殻によって定義される`center`です。殻を作成するアルゴリズムは[こちら](https://www.cmu.edu/biolphys/deserno/pdf/sphere_equi.pdf)で見つけることができます。

## 引数

  * `center::CartesianPoint{T}`: [`NBodyChargeCloud`](@ref)の中心位置。
  * `energy::RealQuantity`: 単位付きの沈着エネルギー。単位が指定されていない場合、値はeVの単位で解析されます。
  * `N::Integer`: [`NBodyChargeCloud`](@ref)内の電荷の概算数（約1%の変動があるかもしれません）。
  * `particle_type`: エネルギーを沈着させた粒子の[`ParticleType`](@ref)。デフォルトは`Gamma`です。

## キーワード

  * `radius::T`: [`NBodyChargeCloud`](@ref)の半径の推定値。デフォルトは`particle_type`から`radius_guess`を介して決定されます。
  * `number_of_shells::Int`: `center`点の周りの殻の数。デフォルトは`2`です。

## 例

```julia
center = CartesianPoint{T}([0,0,0])
energy = 1460u"keV"
NBodyChargeCloud(center, energy, 200, number_of_shells = 3)
```

!!! 注     `energy`に単位付きの値を使用するには、パッケージ[Unitful.jl](https://github.com/PainterQubits/Unitful.jl)が必要です。 ```
