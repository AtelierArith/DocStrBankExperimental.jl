```
sphere_optimize
```

Optimize a given objective fucntion constrained on a unit sphere.

See http://hdl.handle.net/10012/16710 for more detail.

# Arguments

  * `data::Matrix{Float64}`: each row contains an observation.
  * `object_fun::Function`: an arbitrary objective function defined on unit sphere.
  * `n_of_candidate::Int64=5`: number of candidate directions in the fine search step.
  * `unit_sphere=nothing`: the unit spehre can be pre-generated. By default a unit sphere   will be generated automatically.
  * `proj=nothing`: previously found projection directions.    See [`projection_pursuit`](@ref projection_pursuit).
  * `fnscale::Int64=-1`: maximize or minimize the objective function. By default    equals -1, which means maximize objective function. If the objective function   needs to be minimized, set to `fnscale=1`.
  * `par::Bool=true`: run the program in parallel.
  * `fast::Bool=true`: generate the unit sphere using fast algorithm.   See [`gensphere`](@ref gensphere) and [`fastgensphere`](@ref fastgensphere).
