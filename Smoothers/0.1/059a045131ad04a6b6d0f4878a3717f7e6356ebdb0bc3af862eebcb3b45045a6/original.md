Package: Smoothers

```
sma(x, n, center=false)
```

Smooth a vector of data using a simple moving average

# Arguments

  * `x`: Vector of data.
  * `n`: Size of the moving average.
  * `center`: returns a vector of the same size of x with missing values on the tails.

# Returns

Vector of moving average values

# Examples

```julia-repl
julia> sma(1:5,3)
3-element Vector{Float64}:
 2.0
 3.0
 4.0

julia> sma(1:5,3,true)
5-element Vector{Union{Missing, Float64}}:
  missing
 2.0
 3.0
 4.0
  missing
```
