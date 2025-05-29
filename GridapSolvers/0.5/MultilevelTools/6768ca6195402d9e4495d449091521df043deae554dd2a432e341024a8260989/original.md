```
CartesianModelHierarchy(
  ranks::AbstractVector{<:Integer},
  np_per_level::Vector{<:NTuple{D,<:Integer}},
  domain::Tuple,
  nc::NTuple{D,<:Integer};
  nrefs::Union{<:Integer,Vector{<:Integer},Vector{<:NTuple{D,<:Integer}},NTuple{D,<:Integer}},
  map::Function = identity,
  isperiodic::NTuple{D,Bool} = Tuple(fill(false,D)),
  add_labels!::Function = (labels -> nothing),
) where D
```

Returns a `ModelHierarchy` with a Cartesian model as coarsest level. The i-th level    will be distributed among `np_per_level[i]` processors. Two consecutive levels are    refined by a factor of `nrefs[i]`.

## Parameters:

  * `ranks`: Initial communicator. Will be used to generate subcommunicators.
  * `domain`: Tuple containing the domain limits.
  * `nc`: Tuple containing the number of cells in each direction for the coarsest model.
  * `np_per_level`: Vector containing the number of processors we want to distribute each level into. Requires a tuple `np = (np_1,...,np_d)` for each level, then each  level will be distributed among `prod(np)` processors with `np_i` processors in the i-th direction.
  * `nrefs`: Vector containing the refinement factor for each level. Has `nlevs-1` entries,    and each entry can either be an integer (homogeneous refinement) or a tuple    with `D` integers (inhomogeneous refinement).
