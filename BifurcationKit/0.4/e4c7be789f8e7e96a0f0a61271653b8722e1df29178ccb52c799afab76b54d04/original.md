```julia
struct DefaultEig{T} <: BifurcationKit.AbstractDirectEigenSolver
```

The struct `DefaultEig` is used to  provide the `eigen` method to `BifurcationKit`.

## Fields

  * `which::Any`: How do we sort the computed eigenvalues. Default: real

## Constructors

Just pass the above fields like `DefaultEig(; which = abs)`
