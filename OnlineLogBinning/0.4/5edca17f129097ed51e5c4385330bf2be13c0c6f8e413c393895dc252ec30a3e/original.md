```
push!(bacc::BinningAccumulator, itr)
```

`push!` each value of the data stream `itr` through the `BinningAccumulator`.

# Example

```jldoctest
julia> bacc = BinningAccumulator()
BinningAccumulator{Float64} with 0 binning levels.
0th Binning Level (unbinned data):
LevelAccumulator{Float64} with online fields:
    level    = 0
    num_bins = 0
    Taccum   = 0.0
    Saccum   = 0.0
    Paccum   = PairAccumulator{Float64}(true, [0.0, 0.0])

    Calculated Level Statistics:
    Current Mean             = NaN
    Current Variance         = -0.0
    Current Std. Deviation   = -0.0
    Current Var. of the Mean = NaN
    Current Std. Error       = NaN

julia> push!(bacc, [42, -26])
BinningAccumulator{Float64} with 1 binning levels.
0th Binning Level (unbinned data):
LevelAccumulator{Float64} with online fields:
    level    = 0
    num_bins = 2
    Taccum   = 16.0
    Saccum   = 2312.0
    Paccum   = PairAccumulator{Float64}(true, [0.0, 0.0])

    Calculated Level Statistics:
    Current Mean             = 8.0
    Current Variance         = 2312.0
    Current Std. Deviation   = 48.08326112068523
    Current Var. of the Mean = 1156.0
    Current Std. Error       = 34.0

1th Binning Level:
LevelAccumulator{Float64} with online fields:
    level    = 1
    num_bins = 0
    Taccum   = 0.0
    Saccum   = 0.0
    Paccum   = PairAccumulator{Float64}(false, [0.0, 8.0])

    Calculated Level Statistics:
    Current Mean             = NaN
    Current Variance         = -0.0
    Current Std. Deviation   = -0.0
    Current Var. of the Mean = NaN
    Current Std. Error       = NaN

```
