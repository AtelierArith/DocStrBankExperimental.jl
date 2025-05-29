```
EPITrajectory(T, numProfiles, numSamplingPerProfile
              ; TE::T=0.0
              , AQ::T=1.e-3
              , EPI_factor::Int64=1
              , profileOffset= :equispaced
              , kargs...)
```

returns a 2d cartesian trajectory.

# Arguments

  * `numProfiles::Int64`            - number of profiles
  * `numSamplingPerProfile::Int64`  - number of sampling points per profile
  * (`TE::T=0.0`)             - echo time in s
  * (`AQ::T=1.e-3`)           - readout duration in s (per profile)
  * (`EPI_factor::Int64=1`)         - EPI factor, e.g. how many profiles to acquire per shot
  * (`profileOffset= :equispaced`)  - equispaced or random ordering of the shots
