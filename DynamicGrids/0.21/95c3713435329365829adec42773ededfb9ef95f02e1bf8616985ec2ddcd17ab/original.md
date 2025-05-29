```
sim!(output, rules::Rule...; kw...)
sim!(output, rules::Tuple{<:Rule,Vararg}; kw...)
sim!(output, [ruleset::Ruleset=ruleset(output)]; kw...)
```

Runs the simulation rules over the `output` `tspan`, writing the destination array to `output` for each time-step.

# Arguments

  * `output`: An [`Output`](@ref) to store grids or display them on the screen.
  * `ruleset`: A [`Ruleset`](@ref) containing one or more [`Rule`](@ref)s. If the output has a `Ruleset` attached, it will be used.

# Keywords

Theses are the taken from the `output` argument by default:

  * `init`: optional array or NamedTuple of arrays.
  * `mask`: a `Bool` array matching the init array size. `false` cells do not run.
  * `aux`: a `NamedTuple` of auxilary data to be used by rules.
  * `tspan`: a tuple holding the start and end of the timespan the simulaiton will run for.
  * `fps`: the frames per second to display. Will be taken from the output if not passed in.

Theses are the taken from the `ruleset` argument by default:

  * `proc`: a [`Processor`](@ref) to specificy the hardware to run simulations on,    like [`SingleCPU`](@ref), [`ThreadedCPU`](@ref) or [`CuGPU`](@ref) when    KernelAbstractions.jl and a CUDA gpu is available.
  * `opt`: a [`PerformanceOpt`](@ref) to specificy optimisations like   [`SparseOpt`](@ref) or [`NoOpt`](@ref). Defaults to `NoOpt()`.
  * `boundary`: what to do with boundary of grid edges.  Options are [`Remove`](@ref) or [`Wrap`](@ref), defaulting to `Remove()`.
  * `cellsize`: the size of cells, which may be accessed by rules.
  * `timestep`: fixed timestep where this is required for some rules.   eg. `Month(1)` or `1u"s"`.

Other:

  * `simdata`: a [`SimData`](@ref) object. Keeping it between simulations can reduce memory allocation a little, when that is important.
