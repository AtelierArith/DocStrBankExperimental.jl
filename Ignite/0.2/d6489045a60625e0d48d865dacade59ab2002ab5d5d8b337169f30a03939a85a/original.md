```julia
struct State <: AbstractDict{Symbol, Any}
```

Current state of the engine.

`State` is a light wrapper around a `DefaultOrderedDict{Symbol, Any, Nothing}` with the following keys:

  * `:iteration`: the current iteration, beginning with 1.
  * `:epoch`: the current epoch, beginning with 1.
  * `:max_epochs`: The number of epochs to run.
  * `:epoch_length`: The number of batches processed per epoch.
  * `:output`: The output of `process_function` after a single iteration.
  * `:last_event`: The last event fired.
  * `:counters`: A `DefaultOrderedDict{AbstractFiringEvent, Int, Int}(0)` with firing event firing counters.
  * `:times`: An `OrderedDict{AbstractFiringEvent, Float64}()` with total and per-epoch times fetched on firing event keys.

Fields can be accessed and modified using `getproperty` and `setproperty!`. For example, `engine.state.iteration` can be used to access the current iteration, and `engine.state.new_field = value` can be used to store `value` for later use e.g. by an event handler.
