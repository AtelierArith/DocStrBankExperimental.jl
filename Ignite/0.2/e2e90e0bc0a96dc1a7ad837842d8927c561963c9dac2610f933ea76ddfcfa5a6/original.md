```julia
mutable struct Engine{P}
```

An `Engine` struct to be run using [`Ignite.run!`](@ref). Can be constructed via `engine = Engine(process_function; kwargs...)`, where the process function takes two arguments: the parent `engine`, and a batch of data.

Fields: 

  * `process_function::Any`: A function that processes a single batch of data and returns an output.
  * `state::Ignite.State`: An object that holds the current state of the engine.
  * `event_handlers::Vector{Ignite.EventHandler}`: A list of event handlers that are called at specific points when the engine is running.
  * `logger::Union{Nothing, Base.CoreLogging.AbstractLogger}`: An optional logger; if `nothing`, then `current_logger()` will be used.
  * `timer::TimerOutputs.TimerOutput`: Internal timer. Can be used with `TimerOutputs` to record event timings
  * `should_terminate::Bool`: A flag that indicates whether the engine should stop running.
  * `exception::Union{Nothing, Exception}`: Exception thrown during training
