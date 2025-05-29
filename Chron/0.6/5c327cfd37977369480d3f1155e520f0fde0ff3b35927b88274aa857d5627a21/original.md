```julia
StratMetropolisDist(smpl::ChronAgeData, [hiatus::HiatusData,] config::StratAgeModelConfiguration)
```

Runs the main Chron.jl age-depth model routine for a stratigraphic set of samples defined by sample heights and fitted asymmetric age distributions (`BilinearExponential`) in the `smpl` struct, and an age-depth model configuration defined by the `config` struct.

Optionally, if a `hiatus` struct is provided, the model will additionally incorporate information about the durations of known hiatuses at the specified model heights.

### Examples:

```julia
(mdl, agedist, lldist) = StratMetropolisDist(smpl, config)
```

```julia
(mdl, agedist, hiatusdist, lldist) = StratMetropolisDist(smpl, hiatus, config)
```
