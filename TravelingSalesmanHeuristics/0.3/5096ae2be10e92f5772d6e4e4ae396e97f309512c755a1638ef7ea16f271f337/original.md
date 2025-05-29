simulated_annealing(distmat; ...)

Use a simulated annealing strategy to return a closed tour. The temperature decays exponentially from `init_temp` to `final_temp`. Return a tuple `(path, cost)`.

### Optional keyword arguments:

  * `steps::Int = 50n^2`: number of steps to take; defaults to 50n^2 where n is number of cities
  * `num_starts::Int = 1`: number of times to run the simulated annealing algorithm, each time   starting with a random path, or `init_path` if non-null. Defaults to 1.
  * `init_temp::Real = exp(8)`: initial temperature which controls initial chance of accepting an   inferior tour.
  * `final_temp::Real = exp(-6.5)` final temperature which controls final chance of accepting an   inferior tour; lower values roughly correspond to a longer period of 2-opt.
  * `init_path::Union{Vector{Int}, Nothing} = nothing`: path to start the annealing from.   Either a `Vector{Int}` or `nothing`. If a `Vector{Int}` is given, it will be used as the initial path;   otherwise a random initial path is used.
