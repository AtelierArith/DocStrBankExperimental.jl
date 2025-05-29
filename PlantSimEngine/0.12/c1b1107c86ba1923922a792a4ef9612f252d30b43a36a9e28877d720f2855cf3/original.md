```
run!(object, meteo, constants, extra=nothing; check=true, executor=Floops.ThreadedEx())
run!(object, mapping, meteo, constants, extra; nsteps, outputs, check, executor)
```

Run the simulation for each model in the model list in the correct order, *i.e.* respecting the dependency graph.

If several time-steps are given, the models are run sequentially for each time-step.

# Arguments

  * `object`: a [`ModelList`](@ref), an array or dict of `ModelList`, or a plant graph (MTG).
  * `meteo`: a [`PlantMeteo.TimeStepTable`](https://palmstudio.github.io/PlantMeteo.jl/stable/API/#PlantMeteo.TimeStepTable) of

[`PlantMeteo.Atmosphere`](https://palmstudio.github.io/PlantMeteo.jl/stable/API/#PlantMeteo.Atmosphere) or a single `PlantMeteo.Atmosphere`.

  * `constants`: a [`PlantMeteo.Constants`](https://palmstudio.github.io/PlantMeteo.jl/stable/API/#PlantMeteo.Constants) object, or a `NamedTuple` of constant keys and values.
  * `extra`: extra parameters, not available for simulation of plant graphs (the simulation object is passed using this).
  * `check`: if `true`, check the validity of the model list before running the simulation (takes a little bit of time), and return more information while running.
  * `executor`: the [`Floops`](https://juliafolds.github.io/FLoops.jl/stable/) executor used to run the simulation either in sequential (`executor=SequentialEx()`), in a

multi-threaded way (`executor=ThreadedEx()`, the default), or in a distributed way (`executor=DistributedEx()`).

  * `mapping`: a mapping between the MTG and the model list.
  * `nsteps`: the number of time-steps to run, only needed if no meteo is given (else it is infered from it).
  * `outputs`: the outputs to get in dynamic for each node type of the MTG.

# Returns

Modifies the status of the object in-place. Users may retrieve the results from the object using  the [`status`](https://virtualplantlab.github.io/PlantSimEngine.jl/stable/API/#PlantSimEngine.status-Tuple{Any})  function (see examples).

# Details

## Model execution

The models are run according to the dependency graph. If a model has a soft dependency on another model (*i.e.* its inputs are computed by another model), the other model is run first. If a model has several soft dependencies, the parents (the soft dependencies) are always computed first.

## Parallel execution

Users can ask for parallel execution by providing a compatible executor to the `executor` argument. The package will also automatically check if the execution can be parallelized. If it is not the case and the user asked for a parallel computation, it return a warning and run the simulation sequentially. We use the [`Floops`](https://juliafolds.github.io/FLoops.jl/stable/) package to run the simulation in parallel. That means that you can provide any compatible executor to the `executor` argument. You can take a look at [FoldsThreads.jl](https://github.com/JuliaFolds/FoldsThreads.jl) for extra thread-based executors, [FoldsDagger.jl](https://github.com/JuliaFolds/FoldsDagger.jl) for  Transducers.jl-compatible parallel fold implemented using the Dagger.jl framework, and soon [FoldsCUDA.jl](https://github.com/JuliaFolds/FoldsCUDA.jl) for GPU computations  (see [this issue](https://github.com/VirtualPlantLab/PlantSimEngine.jl/issues/22)) and [FoldsKernelAbstractions.jl](https://github.com/JuliaFolds/FoldsKernelAbstractions.jl). You can also take a look at  [ParallelMagics.jl](https://github.com/JuliaFolds/ParallelMagics.jl) to check if automatic parallelization is possible.

# Example

Import the packages: 

```jldoctest run
julia> using PlantSimEngine, PlantMeteo;
```

Load the dummy models given as example in the `Examples` sub-module:

```jldoctest run
julia> using PlantSimEngine.Examples;
```

Create a model list:

```jldoctest run
julia> models = ModelList(Process1Model(1.0), Process2Model(), Process3Model(), status = (var1=1.0, var2=2.0));
```

Create meteo data:

```jldoctest run
julia> meteo = Atmosphere(T=20.0, Wind=1.0, P=101.3, Rh=0.65, Ri_PAR_f=300.0);
```

Run the simulation:

```jldoctest run
julia> outputs_sim = run!(models, meteo);
```

Get the results:

```jldoctest run
julia> (outputs_sim[:var4],outputs_sim[:var6])
([12.0], [41.95])
```
