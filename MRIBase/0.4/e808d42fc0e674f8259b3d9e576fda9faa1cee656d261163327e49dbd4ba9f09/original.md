struct describing a trajectory

# Fields

  * `name::String`                  - name of the trajectory
  * `nodes::Matrix{Float64}`        - sampling locations in k-space.                                   (1.dim <-> dimensions of k-space, 2. dim <-> sampling points)
  * `times::Vector{Float64}`        - sampling times in s
  * `TE::Float64`                   - echo time in s
  * `AQ::Float64``                  - readout duration in s (per profile)
  * `numProfiles::Int64`            - number of profiles
  * `numSamplingPerProfile::Int64`  - number of sampling points per profile
  * `numSlices::Int64`              - number of slices (for 3d trajectories)
  * `cartesian::Bool`               - true if sampling points lie on a cartesian grid
  * `circular::Bool`                - true if kspace is covered in a circular domain
