```
CartesianTrajectory(T, numProfiles, numSamplingPerProfile
              ; TE::T=0.0
              , AQ::T=1.e-3
              , kmin=(-0.5,-0.5)
              , kmax=(0.5,0.5)
              , kargs...)
```

returns a 2d cartesian trajectory.

# Arguments

  * `numProfiles::Int64`            - number of profiles
  * `numSamplingPerProfile::Int64`  - number of sampling points per profile
  * (`TE::Float64=0.0`)             - echo time in s
  * (`AQ::Float64=1.e-3`)           - readout duration in s (per profile)
  * (`kmin=(-0.5,-0.5)`)            - minimum values of the covered k-space (for partial Fourier imaging)
  * (`kmax=(-0.5,-0.5)`)            - maximum values of the covered k-space (for partial Fourier imaging)
