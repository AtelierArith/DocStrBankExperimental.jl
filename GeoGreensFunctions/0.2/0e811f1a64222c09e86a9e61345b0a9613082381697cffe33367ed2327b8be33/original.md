```
dc3d(x::T, y::T, z::T, α::T, dep::T, dip::T,
    al::Union{A, SubArray}, aw::Union{A, SubArray}, disl::A
    ) where {T <: Number, A <: AbstractVecOrMat{T}}
```

Calculate displacements and gradient of displacements due to a rectangular dislocation     in an elastic isotropic halfspace.

Please see [dc3d](http://www.bosai.go.jp/study/application/dc3d/DC3Dhtml_E.html) for details.     Also this fault coordinate system is widely used in this package.

## Arguments

  * `x`, `y`, `z`: observational position, where $z ≤ 0$
  * `α`: elastic constant
  * `dep`: depth of fault origin
  * `dip`: dip angle in degree
  * `al`: a vector of 2 numbers, indicating along strike (x-axis) spanning
  * `aw`: a vector of 2 numbers, indicating along downdip (y-z plane) spanning
  * `disl`: a vector of 3 numbers, indicating dislocation in along-strike,   along-downdip and tensile respectively.

## Output

A vector of 12 numbers, each is $u_{x}$, $u_{y}$, $u_{z}$, $u_{x,x}$,     $u_{y,x}$, $u_{z,x}$, $u_{x,y}$, $u_{y,y}$, $u_{z,y}$, $u_{x,z}$     $u_{y,z}$, $u_{z,z}$.
