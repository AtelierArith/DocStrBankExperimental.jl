```
ipf(X::AbstractArray{<:Real}, mar::ArrayMargins; maxiter::Int = 1000, tol::Float64 = 1e-10)
ipf(X::AbstractArray{<:Real}, mar::Vector{<:Vector{<:Real}})
ipf(mar::ArrayMargins)
ipf(mar::Vector{<:Vector{<:Real}})
```

Perform iterative proportional fitting (factor method). The array (X) can be any number of dimensions, and the margins can be multidimensional as well.  If only the margins are given, then the seed matrix `X` is assumed to be an array filled with ones of the correct size and element type.

If the margins are not an ArrayMargins object, they will be coerced to this type.

This function returns the update matrix as an ArrayFactors object. To compute the updated matrix, use `Array(result) .* X` (see examples).

see also: [`ArrayFactors`](@ref), [`ArrayMargins`](@ref)

# Arguments

  * `X::AbstractArray{<:Real}`: Array to be adjusted
  * `mar::ArrayMargins`: Target margins as an ArrayMargins object
  * `maxiter::Int=1000`: Maximum number of iterations
  * `tol::Float64=1e-10`: Factor change tolerance for convergence

# Examples

```julia-repl
julia> X = [40 30 20 10; 35 50 100 75; 30 80 70 120; 20 30 40 50]
julia> u = [150, 300, 400, 150]
julia> v = [200, 300, 400, 100]
julia> AF = ipf(X, [u, v])
Factors for 2D array:
    [1]: [0.9986403503185242, 0.8833622306385376, 1.1698911437112522, 0.8895042701910321]
    [2]: [1.616160156063788, 1.5431801747375655, 1.771623700829941, 0.38299396265192226]

julia> Z = Array(AF) .* X
4×4 Matrix{Float64}:
 64.5585   46.2325   35.3843   3.82473
 49.9679   68.1594  156.499   25.3742
 56.7219  144.428   145.082   53.7673
 28.7516   41.18     63.0347  17.0337

julia> ArrayMargins(Z)
Margins of 2D array:
  [1]: [150.0000000009452, 299.99999999962523, 399.99999999949796, 149.99999999993148]
  [2]: [200.0, 299.99999999999994, 399.99999999999994, 99.99999999999997]
```
