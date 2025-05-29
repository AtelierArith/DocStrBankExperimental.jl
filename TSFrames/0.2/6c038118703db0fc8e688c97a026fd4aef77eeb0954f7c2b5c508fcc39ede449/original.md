# Size methods

```julia
ncol(ts::TSFrame)
```

Return the number of columns of `ts`. `nc` is an alias for `ncol`.

# Examples

```jldoctest; setup = :(using TSFrames, DataFrames, Dates, Random, Statistics)
julia> using Random;

julia> random(x) = rand(MersenneTwister(123), x);

julia> TSFrames.ncol(TSFrame([random(100) random(100) random(100)]))
3

julia> nc(TSFrame([random(100) random(100) random(100)]))
3
```
