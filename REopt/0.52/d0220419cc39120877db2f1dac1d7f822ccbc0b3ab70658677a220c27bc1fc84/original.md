```
backup_reliability(r::Dict)
```

Return dictionary of backup reliability results.

# Arguments

  * `r::Dict`: Dictionary of inputs for reliability calculations. If r not included then uses all defaults.

Possible keys in r: -critical*loads*kw::Array                               Critical loads per time step. (Required input) -microgrid*only::Bool                                   Boolean to check if only microgrid runs during grid outage (defaults to false) -chp*size*kw::Real                                      CHP capacity.  -pv*size*kw::Real                                       Size of PV System -pv*production*factor*series::Array                     PV production factor per time step (required if pv*size*kw in dictionary) -pv*migrogrid*upgraded::Bool                            If true then PV runs during outage if microgrid*only = TRUE (defaults to false) -battery*size*kw::Real                                  Battery capacity. If no battery installed then PV disconnects from system during outage -battery*size*kwh::Real                                 Battery energy storage capacity -battery*charge*efficiency::Real                        Battery charge efficiency -battery*discharge*efficiency::Real                     Battery discharge efficiency -battery*starting*soc*series*fraction::Array            Battery percent state of charge time series during normal grid-connected usage -generator*failure*to*start::Real = 0.0094              Chance of generator starting given outage -generator*mean*time*to*failure::Real = 1100            Average number of time steps between a generator's failures. 1/(failure to run probability).  -num*generators::Int = 1                                Number of generators.  -generator*size*kw::Real = 0.0                          Backup generator capacity.  -num*battery*bins::Int = num*battery*bins*default(r[:battery*size*kw],r[:battery*size*kwh])     Number of bins for discretely modeling battery state of charge -max*outage*duration::Int = 96                          Maximum outage duration modeled
