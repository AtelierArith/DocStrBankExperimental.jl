```
backup_reliability(d::Dict, p::REoptInputs, r::Dict)
```

Return dictionary of backup reliability results.

# Arguments

  * `d::Dict`: REopt results dictionary.
  * `p::REoptInputs`: REopt Inputs Struct.
  * `r::Dict`: Dictionary of inputs for reliability calculations. If r not included then uses all defaults.

Possible keys in r:     -generator*operational*availability::Real = 0.995       Fraction of year generators not down for maintenance     -generator*failure*to*start::Real = 0.0094              Chance of generator starting given outage     -generator*mean*time*to*failure::Real = 1100            Average number of time steps between a generator's failures. 1/(failure to run probability).      -num*generators::Int = 1                                Number of generators.     -generator*size*kw::Real = 0.0                          Backup generator capacity.      -num*battery*bins::Int = depends on battery sizing      Number of bins for discretely modeling battery state of charge     -battery*operational*availability::Real = 0.97          Likelihood battery will be available at start of outage            -pv*operational*availability::Real = 0.98               Likelihood PV will be available at start of outage     -wind*operational*availability::Real = 0.97             Likelihood Wind will be available at start of outage     -max*outage*duration::Int = 96                          Maximum outage duration modeled     -microgrid_only::Bool = false                           Determines how generator, PV, and battery act during islanded mode
