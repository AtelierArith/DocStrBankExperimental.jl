struct describing MRI acquisition data.

# Fields

  * `sequenceInfo::Dict{Symbol,Any}`          - additional information on the pulse sequence
  * `traj::Vector{Trajectory}`                - trajectories for each echo/contrast
  * `kdata::Array{Matrix{Complex{<:AbstractFloat}},3}`      - each matrix contains data for one trajectory                                             (1. dim k-space nodes, 2. dim coils)                                             the outer dims describe:                                             1. dim echoes, 2. dim slices, 3. dim repetitions
  * `subsampleIndices::Vector{Array{Int64}}`  - indices sampled for each echo/contrast
  * `encodingSize::Vector{Int64}`             - size of the underlying image matrix
  * `fov::Vector{Float64}`                    - field of view in mm
