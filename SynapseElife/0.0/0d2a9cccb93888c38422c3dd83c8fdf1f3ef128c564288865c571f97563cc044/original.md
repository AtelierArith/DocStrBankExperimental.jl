```julia
struct PreSynapseParams
```

# Presynaptic parameters

  * Firing events are processed separately from the main simulation (at `src/OnlyStp.jl`) it takes the firing structure as input from the function [`firingPattern`](@ref).
  * Using the presynaptic stimulation times, the vesicle depletion and AP induced by EPSP are estimated, however one can use a tag to deactivate it (covering sub-threshold EPSP cases) as in  [`dataProtocol`](@ref).
  * The presynaptic part of our model is phenomenological, for instance, the variable `Soma` in `src/OnlyStp.jl:38` was made to represent the voltage and can accumulate for faster frequencies but has an abstract unit.

# Equations

based on D. Sterratt et al book; [`Principles of Computational Modelling in Neuroscience`](https://www.compneuroprinciples.org/ ) page 183 

raterec  = (`R_0` - `R`) ⋅ τ_R ⋅ `rrp` 

raterrp  = (`D_0` - `D`) ⋅ τ_D ⋅ `rec` 

rateref  = (`R_0` - `R`) ⋅ ref_dt 

# Fields

  * `τ_rec`: recovery constant of pre calcium decay function Default: 20000
  * `δ_ca`: fraction of decay constant of pre calcium decay f Default: 0.0004
  * `τ_pre`: decay time constant of pre calcium Default: 20
  * `τ_V`: decay time constant for AP induced by EPSP Default: 40
  * `δ_delay_AP`: delay to EPSPs onset and evoked AP Default: 15.0
  * `D_0`: initial conditions ready releaseble pool Default: 25
  * `R_0`: initial conditions recovery pool Default: 30
  * `τ_R`: rate for `D -> R` Default: 5000
  * `τ_D`: rate for `R -> D` Default: 45000
  * `τ_R_ref`: rate for `infinite reservoir -> R` Default: 40000
  * `s`: sigmoid parameter for release probability Default: 2.0
  * `h`: sigmoid parameter for release probability Default: 0.7
  * `sampling_rate`: sampling rate for plotting / printing Default: 1.0
