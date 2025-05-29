```
push!(bacc::BinningAccumulator, value::Number)
```

Add a single `value` from the data stream into the online binning analysis. The single value enters at the bin at the lowest level. 

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

julia> push!(bacc, 42)
BinningAccumulator{Float64} with 0 binning levels.
0th Binning Level (unbinned data):
LevelAccumulator{Float64} with online fields:
    level    = 0
    num_bins = 0
    Taccum   = 0.0
    Saccum   = 0.0
    Paccum   = PairAccumulator{Float64}(false, [0.0, 42.0])        

    Calculated Level Statistics:
    Current Mean             = NaN
    Current Variance         = -0.0
    Current Std. Deviation   = -0.0
    Current Var. of the Mean = NaN
    Current Std. Error       = NaN

```

!!! note
    Notice that the `Taccum` and `Saccum` remain zero while `num_bins == 0`.  These are only accumulated for each input pair. Or once `Paccum.fullpair == true`.

