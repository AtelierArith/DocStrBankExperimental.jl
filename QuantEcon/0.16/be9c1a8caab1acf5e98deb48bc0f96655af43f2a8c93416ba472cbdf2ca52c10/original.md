Integrate the d-dimensional function `f` on a rectangle with lower and upper bound for dimension i defined by `a[i]` and `b[i]`, respectively; using `n[i]` points.

##### Arguments

  * `f::Function` The function to integrate over. This should be a function that accepts as its first argument a matrix representing points along each dimension (each dimension is a column). Other arguments that need to be passed to the function are caught by `args...` and `kwargs...``
  * `n::Union{Int, Vector{Int}}` : Number of desired nodes along each dimension
  * `a::Union{Real, Vector{Real}}` : Lower endpoint along each dimension
  * `b::Union{Real, Vector{Real}}` : Upper endpoint along each dimension
  * `kind::AbstractString("lege")` Specifies which type of integration to perform. Valid values are:

      * `"lege"` : Gauss-Legendre
      * `"cheb"` : Gauss-Chebyshev
      * `"trap"` : trapezoid rule
      * `"simp"` : Simpson rule
      * `"N"` : Neiderreiter equidistributed sequence
      * `"W"` : Weyl equidistributed sequence
      * `"H"` : Haber  equidistributed sequence
      * `"R"` : Monte Carlo
      * `args...(Void)`: additional positional arguments to pass to `f`
      * `;kwargs...(Void)`: additional keyword arguments to pass to `f`

##### Returns

  * `out::Float64` : The scalar that approximates integral of `f` on the hypercube formed by `[a, b]`

##### References

Miranda, Mario J, and Paul L Fackler. Applied Computational Economics and Finance, MIT Press, 2002.
