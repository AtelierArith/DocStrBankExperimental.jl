```
SpiralTrajectory(numProfiles, numSamplingPerProfile
              ; TE::Float64=0.0
              , AQ::Float64=1.e-3
              , windings::Real= 6.25
              , angleOffset= :equispaced
              , kargs...)
```

returns a 2d spiral trajectory.

# Arguments

  * `numProfiles::Int64`            - number of profiles
  * `numSamplingPerProfile::Int64`  - number of sampling points per profile
  * (`TE::Float64=0.0`)             - echo time in s
  * (`AQ::Float64=1.e-3`)           - readout duration in s (per profile)
  * (`windings::Real= 6.25`)        - number of windings of the spiral profiles
  * (`angleOffset= :equispaced`)    - spacing of profile angles (`:equispaced` sampling, `:golden` angle sampling or `:random` sampling)
