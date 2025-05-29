```
trajectory(trajName::AbstractString, numProfiles::Int, numSamplingPerProfile::Int; numSlices::Int64=1, TE::Float64=0.0, AQ::Float64=1.e-3, kargs...)
```

is a factory method to construct a trajectory from its `name`

# Arguments

  * `name::String`                  - name of the trajectory
  * `numProfiles::Int64`            - number of profiles
  * `numSamplingPerProfile::Int64`  - number of sampling points per profile
  * (`numSlices::Int64=1`)          - number of slices (for 3d trajectories)
  * (`TE::Float64=0.0`)             - echo time in s
  * (`AQ::Float64=1.e-3`)           - readout duration in s (per profile)
  * `kargs...`                      - addional keyword arguments
