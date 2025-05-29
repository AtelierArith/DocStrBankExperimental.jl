```
StackOfStarsTrajectory(numProfiles, numSamplingPerProfile
              ; TE::Float64=0.0
              , AQ::Float64=1.e-3
              , numSlices=1
              , angleOffset= :equispaced
              , kargs...)
```

returns a 2d radial trajectory.

# Arguments

  * `numProfiles::Int64`            - number of profiles
  * `numSamplingPerProfile::Int64`  - number of sampling points per profile
  * (`TE::Float64=0.0`)             - echo time in s
  * (`AQ::Float64=1.e-3`)           - readout duration in s (per profile)
  * (`numSlices=1`)                 - number of slices
  * (`angleOffset= :equispaced`)    - spacing of profile angles (`:equispaced` sampling, `:golden` angle sampling or `:random` sampling)
