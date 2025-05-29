```
Grid(ID, name, T, N, r, r′, r′′, h, r0, epn, epw, k, p, polynom)
```

Type with fields:

  * `.ID`:    grid identifer name (`::Int`)
  * `.name`:  grid identifer name (`::String`)
  * `.T`:     gridtypename (`::Type`)
  * `.N`:     number of grid points (`::Int`)
  * `.r`:   tabulated grid function (`::Vector{T}`)
  * `.r′`:   tabulated first derivative of grid function (`::Vector{T}`)
  * `.r′′`:   tabulated second derivative of grid function (`::Vector{T}`)
  * `.h` :    grid step multiplyer (`::T`)
  * `.r0`:    grid scale factor (`::T`)
  * `.epn`:   number of endpoints used for trapezoidal endpoint correction (must be odd) (`::Int`)
  * `.epw`:   trapezoidal endpoint weights for n=1:epn (`::Vector{Vector{T}}`)
  * `.k`:     finite-difference order (`::Int`)
  * `.p`:     only for truncated-exponential grid; truncation power (`::Int`)
  * `.polynom`: only for polynomial grid: polynom (`::Vector{T}`)

The object `Grid` is best created with the function [`castGrid`](@ref).
