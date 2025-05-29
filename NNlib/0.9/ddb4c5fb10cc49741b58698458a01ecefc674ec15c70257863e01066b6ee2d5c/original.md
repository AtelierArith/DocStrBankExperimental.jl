```
dropout([rng], A, p; [dims])
```

Returns an array in which each element of `A` is either replaced with zero, with probability `p`, or else multiplied by `1/(1-p)`.

By default every element is treated independently. With keyword `dims=1`, a choice is made for every value of the 1st index i.e. each row of a matrix is either zero or not.

Optional first argument is the random number generator used.

# Examples

```julia-repl
julia> dropout(ones(2, 10), 0.2)
2×10 Matrix{Float64}:
 1.25  1.25  0.0   1.25  1.25  1.25  1.25  1.25  1.25  1.25
 1.25  1.25  1.25  0.0   1.25  1.25  0.0   1.25  1.25  1.25

julia> mean(dropout(ones(10^4, 5), 0.2), dims=1)
1×5 Matrix{Float64}:
 0.998  1.00075  0.99125  0.99575  1.00075

julia> dropout(ones(5, 5), 0.7, dims=1)  # whole row the same
5×5 Matrix{Float64}:
 3.33333  3.33333  3.33333  3.33333  3.33333
 0.0      0.0      0.0      0.0      0.0
 0.0      0.0      0.0      0.0      0.0
 3.33333  3.33333  3.33333  3.33333  3.33333
 0.0      0.0      0.0      0.0      0.0

julia> mean(dropout(ones(10^4, 5), 0.3, dims=1), dims=1)
1×5 Matrix{Float64}:
 1.00571  1.00571  1.00571  1.00571  1.00571
```
