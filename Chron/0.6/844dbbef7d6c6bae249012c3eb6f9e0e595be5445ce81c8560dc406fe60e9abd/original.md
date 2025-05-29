```julia
StratMetropolis(smpl::ChronAgeData, [hiatus::HiatusData,] config::StratAgeModelConfiguration)
StratMetropolis(smpl::GeneralAgeData, [hiatus::HiatusData,] config::StratAgeModelConfiguration)
```

Runs the main Chron.jl age-depth model routine for a stratigraphic set of samples defined by sample heights and simple Gaussian age constraints in the `smpl` struct, and an age-depth model configuration defined by the `config` struct.

Optionally, if a `hiatus` struct is provided, the model will additionally incorporate information about the durations of known hiatuses at the specified model heights.

### Examples:

```julia
(mdl, agedist, lldist) = StratMetropolis(smpl, config)
```

```julia
(mdl, agedist, hiatusdist, lldist) = StratMetropolis(smpl, hiatus, config)
```
