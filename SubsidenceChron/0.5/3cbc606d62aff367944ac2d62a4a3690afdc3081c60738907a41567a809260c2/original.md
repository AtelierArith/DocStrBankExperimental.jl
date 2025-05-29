```julia
SubsidenceStratMetropolis(smpl::ChronAgeData, config::StratAgeModelConfiguration, therm::ThermalSubsidenceParameters, subsidence_strat_depths, Sμ, Sσ, beta_ip, t0_ip;
    subsidencebotom=minimum(smpl.Height),
    subsidencetop=maximum(smpl.Height),
    lithosphere = Normal(125000, 100),
)
```

Runs the main SubsidenceChron.jl age-depth model routine given a set of Gaussian age constraints specified in the `smpl` struct, an age-depth model configuration specified in the `config` struct, thermal subsidence parameters defined in the `therm` struct, decompation and backstripping outputs in the form of `subsidence_strat_depths`, `Sμ`, and `Sσ`, and prior estimates for stretching factor Beta (`beta_ip`) and time of thermal subsedence onset (`t0_ip`).

### Examples:

```julia
(subsmdl, agedist, lldist, beta_t0dist, lldist_burnin) = SubsidenceStratMetropolis(smpl, config, therm, subsidence_strat_depths, Sμ, Sσ_corr, Beta_sigma/10, T0_sigma/10)
```
