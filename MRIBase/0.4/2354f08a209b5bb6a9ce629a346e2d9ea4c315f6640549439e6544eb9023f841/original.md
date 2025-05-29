```
KooshballTrajectory(numProfiles, numSamplingPerProfile
              ; TE::Float64=0.0
              , AQ::Float64=1.e-3
              , kargs...)
```

returns a 3d kooshball trajectory.

# Arguments

  * `numProfiles::Int64`            - number of profiles
  * `numSamplingPerProfile::Int64`  - number of sampling points per profile
  * (`TE::Float64=0.0`)             - echo time in s
  * (`AQ::Float64=1.e-3`)           - readout duration in s (per profile)
