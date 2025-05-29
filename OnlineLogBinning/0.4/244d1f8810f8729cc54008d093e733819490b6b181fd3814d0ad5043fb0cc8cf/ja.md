```
push!(bacc::BinningAccumulator, value::Number)
```

データストリームからの単一の `value` をオンラインビニング分析に追加します。単一の値は最も低いレベルのビンに入ります。

# 例

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
    `num_bins == 0` の間、`Taccum` と `Saccum` がゼロのままであることに注意してください。これらは各入力ペアのためにのみ蓄積されます。あるいは `Paccum.fullpair == true` の場合です。

