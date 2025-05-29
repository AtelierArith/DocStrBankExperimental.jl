A hook is called at different stage during a [`run`](@ref) to allow users to inject customized runtime logic. By default, an `AbstractHook` will do nothing. One can customize the behavior by implementing the following methods:

  * `Base.push!(hook::YourHook, ::PreActStage, agent, env)`
  * `Base.push!(hook::YourHook, ::PostActStage, agent, env)`
  * `Base.push!(hook::YourHook, ::PreEpisodeStage, agent, env)`
  * `Base.push!(hook::YourHook, ::PostEpisodeStage, agent, env)`
  * `Base.push!(hook::YourHook, ::PostExperimentStage, agent, env)`

By convention, the `Base.getindex(h::YourHook)` is implemented to extract the metrics we are interested in. Users can compose different `AbstractHook`s with `+`.
