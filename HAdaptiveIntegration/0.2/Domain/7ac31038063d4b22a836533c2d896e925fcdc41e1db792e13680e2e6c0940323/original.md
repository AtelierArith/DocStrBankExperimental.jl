```
struct Simplex{D,T,N} <: AbstractDomain{D,T}
```

A simplex in `D` dimensions with `N=D+1` vertices of element type `T`.

## Fields:

  * `vertices::SVector{N,SVector{D,T}}`: vertices of the simplex.

## Invariants (**not** check at construction):

  * `N = D+1`

## Constructors:

  * `Simplex(vertices...)`
  * `Simplex{T}(vertices...)`
  * `Simplex(vertices::SVector{N,SVector{D,T}})`
