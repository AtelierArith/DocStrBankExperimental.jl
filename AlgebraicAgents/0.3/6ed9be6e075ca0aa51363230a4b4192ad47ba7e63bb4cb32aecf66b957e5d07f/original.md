```
Opera(uuid2agent_pairs...)
```

A dynamic structure that 

  * contains a **directory of agents** (dictionary of `uuid => agent` pairs);
  * keeps track of, and executes, **futures (delayed interactions)**;
  * keeps track of, and executes, **system controls**;
  * keeps track of, and executes, **instantious interactions**;

# Futures

You may schedule function calls, to be executed at predetermined points of time. An action is modeled as a tuple `(id, call, time)`, where `id` is an optional textual identifier of the action and `call` is a (parameterless) anonymous function, which will be called at the given `time`. Once the action is executed, the return value with corresponding action id and execution time is added to `futures_log` field of `Opera` instance.

See [`add_future!`](@ref) and [`@future`](@ref).

## Example

```julia
alice = MyAgentType("alice")
interact = agent -> wake_up!(agent)
@future alice 5.0 interact(alice) "alice_schedule"
```

The solver will stop at `t=5` and call the function `() -> interact(alice)` (a closure is taken at the time when `@future` is invoked). This interaction is identified as `"alice_schedule"`.

# Control Interactions

You may schedule control function calls, to be executed at every step of the model. An action is modeled as a tuple `(id, call)`, where `id` is an optional textual identifier of the action, and `call` is a (parameterless) anonymous function. Once the action is executed, the return value with corresponding action id and execution time is added to `controls_log` field of `Opera` instance.

See [`add_control!`](@ref) and [`@control`](@ref).

## Example

```julia
system = MyAgentType("system")
control = agent -> agent.temp > 100 && cool!(agent)
@control system control(system) "temperature control"
```

At each step, the solver will call the function `() -> control(system)` (a closure is taken at the time when `@future` is invoked).

# Instantious Interactions

You may schedule additional interactions which exist within a single step of the model; such actions are modeled as named tuples `(id, priority=0., call)`. Here, `call` is a (parameterless) anonymous function.

They exist within a single step of the model and are executed after the calls to `_prestep!` and `_step!` finish, in the order of the assigned priorities.

In particular, you may schedule interactions of two kinds:

  * `poke(agent, priority)`, which will translate into a call `() -> _interact!(agent)`, with the specified priority,
  * `@call opera expresion priority`, which will translate into a call `() -> expression`, with the specified priority.

See [`poke`](@ref) and [`@call`](@ref).

## Examples

```julia
# `poke`
poke(agent, 1.) # call `_interact!(agent)`; this call is added to the instantious priority queue with priority 1
```

```julia
# `@call`
bob_agent = only(getagent(agent, r"bob"))
@call agent wake_up(bob_agent) # translates into `() -> wake_up(bob_agent)` with priority 0
```
