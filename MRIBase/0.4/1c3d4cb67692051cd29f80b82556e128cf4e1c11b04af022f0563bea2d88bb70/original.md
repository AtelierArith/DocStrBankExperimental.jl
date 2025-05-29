```
SpiralTrajectoryVarDens(numProfiles, numSamplingPerProfile
              ; TE::Float64=0.0
              , AQ::Float64=1.e-3
              , windings::Real= 6.25
              , alpha=2.0
              , angleOffset= :equispaced
              , kargs...)
```

returns a 2d spiral trajectory with variable density

# Arguments

  * `numProfiles::Int64`            - number of profiles
  * `numSamplingPerProfile::Int64`  - number of sampling points per profile
  * (`TE::Float64=0.0`)             - echo time in s
  * (`AQ::Float64=1.e-3`)           - readout duration in s (per profile)
  * (`windings::Real= 6.25`)        - number of windings of the spiral profiles
  * (`alpha=2.0`)                   - exponent describing the evolution of the magnitude of the sampling points along the profiles
  * (`angleOffset= :equispaced`)    - spacing of profile angles (`:equispaced` sampling, `:golden` angle sampling or `:random` sampling)
