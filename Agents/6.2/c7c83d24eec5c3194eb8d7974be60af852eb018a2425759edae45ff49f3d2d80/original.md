```
run!(model::ABM, t::Union{Real, Function}; kwargs...)
```

Run the model (evolve via [`step!`](@ref)`(model, t)`) while at the same time collecting data specified by the keywords, explained one by one below. Return the data as two `DataFrame`s, `agent_df, model_df`, one for agent-level data and one for model-level data.

See also [`offline_run!`](@ref) to write data to file while running the model.

## Data-deciding keywords

  * `adata::Vector` means "agent data to collect". If an entry is a `Symbol`, e.g. `:weight`, then the data for this entry is agent's field `weight`. If an entry is a `Function`, e.g. `f`, then the data for this entry is just `f(a)` for each agent `a`. The resulting dataframe columns are named with the input symbol (here `:weight, :f`).
  * `adata::Vector{<:Tuple}`: if `adata` is a vector of tuples instead, data aggregation is done over the agent properties.

    For each 2-tuple, the first entry is the "key" (any entry like the ones mentioned above, e.g. `:weight, f`). The second entry is an aggregating function that aggregates the key, e.g. `mean, maximum`. So, continuing from the above example, we would have `adata = [(:weight, mean), (f, maximum)]`.

    It's also possible to provide a 3-tuple, with the third entry being a conditional function (returning a `Bool`), which assesses if each agent should be included in the aggregate. For example: `x_pos(a) = a.pos[1]>5` with `(:weight, mean, x_pos)` will result in the average weight of agents conditional on their x-position being greater than 5.

    The resulting data name columns use the function [`dataname`](@ref). They create something like `:mean_weight` or `:maximum_f_x_pos`. In addition, you can use anonymous functions in a list comprehension to assign elements of an array into different columns: `adata = [(a)->(a.interesting_array[i]) for i=1:N]`. Column names can also be renamed with `DataFrames.rename!` after data is collected.

    **Notice:** Aggregating only works if there are agents to be aggregated over. If you remove agents during model run, you should modify the aggregating functions. *E.g.* instead of passing `mean`, pass `mymean(a) = isempty(a) ? 0.0 : mean(a)`.
  * `mdata::Vector` means "model data to collect" and works exactly like `adata`. For the model, no aggregation is possible (nothing to aggregate over).

    Alternatively, `mdata` can also be a function. This is a "generator" function, that accepts `model` as input and provides a `Vector` that represents `mdata`. Useful in combination with an [`ensemblerun!`](@ref) call that requires a generator function.

By default both keywords are `nothing`, i.e. nothing is collected/aggregated.

## Mixed-Models

For mixed-models, the `adata` keyword has some additional options & properties. An additional column `agent_type` will be placed in the output dataframe.

In the case that data is needed for one agent type that does not exist in a second agent type, `missing` values will be added to the dataframe.

**Warning:** Since this option is inherently type unstable, try to avoid this in a performance critical situation.

Aggregate functions will fail if `missing` values are not handled explicitly. If `a1.weight` but `a2` (type: Agent2) has no `weight`, use `a2(a) = a isa Agent2; adata = [(:weight, sum, a2)]` to filter out the missing results.

## Other keywords

  * `when = 1`: at which times to perform the data collection and processing. A lot of flexibility is offered based on the type of `when`. Let `t = abmtime(model)` (which is updated throughout the `run!` process).

      * `when::Real`: data are collected each time the model is evolved for at least `when` units of time. For discrete time models like [`StandardABM`](@ref) this must be an integer and in essence it means how many steps to evolve between each data collection. For continuous time models like [`EventQueueABM`](@ref) `when` is the *least* amount of time to evolve the model (with maximum being until an upcoming event is triggered).
      * `when::AbstractVector`: data are collected for `t ∈ when`.
      * `when::Function`: data are collected whenever `when(model, t)` returns `true`.
  * `when_model = when`: same as `when` but for model data.
  * `init = true`: Whether to collect data at the initial model state before it is stepped.
  * `dt = 0.01`: minimum stepping time for continuous time models between data collection checks of `when` and possible data recording time. If `when isa Real` then it must hold `dt ≤ minimum(when, when_model)`. This keyword is ignored for discrete time models as it is 1 by definition.
  * `obtainer = identity`: method to transfer collected data to the `DataFrame`. Typically only change this to [`copy`](https://docs.julialang.org/en/v1/base/base/#Base.copy) if some data are mutable containers (e.g. `Vector`) which change during evolution, or [`deepcopy`](https://docs.julialang.org/en/v1/base/base/#Base.deepcopy) if some data are nested mutable containers. Both of these options have performance penalties.
  * `showprogress=false`: Whether to show progress.
