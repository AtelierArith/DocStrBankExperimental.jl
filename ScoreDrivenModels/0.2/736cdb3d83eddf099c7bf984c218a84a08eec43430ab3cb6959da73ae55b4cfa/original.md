```
ScoreDrivenModel
```

The constructor of a score-driven model. The model receives the lag structure, the distribution and the scaling. You can define the lag structure in two different ways, either by passing integers `p` and `q` to add all lags from `1` to `p` and `1` to `q` or by passing vectors of integers `ps` and `qs` containing the desired lags. Once you build the model all of the unknown parameters that must be estimated are represented as `NaN`.

```jldoctest
# Passing p and q
julia> ScoreDrivenModel(2, 2, LogNormal, 0.5)
ScoreDrivenModel{LogNormal,Float64}([NaN, NaN], Dict(2=>[NaN 0.0; 0.0 NaN],1=>[NaN 0.0; 0.0 NaN]), Dict(2=>[NaN 0.0; 0.0 NaN],1=>[NaN 0.0; 0.0 NaN]), 0.5)

# Passing ps and qs
julia> ScoreDrivenModel([1, 12], [1, 12], Gamma, 0.0)
ScoreDrivenModel{Gamma,Float64}([NaN, NaN], Dict(12=>[NaN 0.0; 0.0 NaN],1=>[NaN 0.0; 0.0 NaN]), Dict(12=>[NaN 0.0; 0.0 NaN],1=>[NaN 0.0; 0.0 NaN]), 0.0)
```

If you don't want all the parameters to be considered time-varying you can express it through the keyword argument `time_varying_params`, there you should pass a vector containing a number that represents which parameter should be time-varying. As an example in the Normal distribution `time_varying_params = [1]` indicates that only $\mu$ is time-varying. You can find the table with the dictionary (number => parameter) in the section [ScoreDrivenModels distributions](@ref).

```jldoctest
julia> ScoreDrivenModel([1, 12], [1, 12], Normal, 1.0; time_varying_params = [1])
ScoreDrivenModel{Normal,Float64}([NaN, NaN], Dict(12=>[NaN 0.0; 0.0 0.0],1=>[NaN 0.0; 0.0 0.0]), Dict(12=>[NaN 0.0; 0.0 0.0],1=>[NaN 0.0; 0.0 0.0]), 1.0)
```
