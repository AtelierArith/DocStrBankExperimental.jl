```
pairwise!(f, dest::AbstractMatrix, x[, y];
          symmetric::Bool=false, skipmissing::Symbol=:none)
```

Store in matrix `dest` the result of applying `f` to all possible pairs of entries in iterators `x` and `y`, and return it. Rows correspond to entries in `x` and columns to entries in `y`, and `dest` must therefore be of size `length(x) × length(y)`. If `y` is omitted then `x` is crossed with itself.

As a special case, if `f` is `cor`, diagonal cells for which entries from `x` and `y` are identical (according to `===`) are set to one even in the presence `missing`, `NaN` or `Inf` entries.

# Keyword arguments

  * `symmetric::Bool=false`: If `true`, `f` is only called to compute for the lower triangle of the matrix, and these values are copied to fill the upper triangle. Only allowed when `y` is omitted. Defaults to `true` when `f` is `cor` or `cov`.
  * `skipmissing::Symbol=:none`: If `:none` (the default), missing values in inputs are passed to `f` without any modification. Use `:pairwise` to skip entries with a `missing` value in either of the two vectors passed to `f` for a given pair of vectors in `x` and `y`. Use `:listwise` to skip entries with a `missing` value in any of the vectors in `x` or `y`; note that this might drop a large part of entries. Only allowed when entries in `x` and `y` are vectors.

# Examples

```jldoctest
julia> using StatsBase, Statistics

julia> dest = zeros(3, 3);

julia> x = [1 3 7
            2 5 6
            3 8 4
            4 6 2];

julia> pairwise!(cor, dest, eachcol(x));

julia> dest
3×3 Matrix{Float64}:
  1.0        0.744208  -0.989778
  0.744208   1.0       -0.68605
 -0.989778  -0.68605    1.0

julia> y = [1 3 missing
            2 5 6
            3 missing 2
            4 6 2];

julia> pairwise!(cor, dest, eachcol(y), skipmissing=:pairwise);

julia> dest
3×3 Matrix{Float64}:
  1.0        0.928571  -0.866025
  0.928571   1.0       -1.0
 -0.866025  -1.0        1.0
```
