```
@process(process::String, doc::String=""; verbose::Bool=true)
```

This macro generate the abstract type and some boilerplate code for the simulation of a process, along  with its documentation. It also prints out a short tutorial for implementing a model if `verbose=true`.

The abstract process type is then used as a supertype of all models implementations for the  process, and is named "Abstract<ProcessName>Model", *e.g.* `AbstractGrowthModel` for a process called growth.

The first argument to `@process` is the new process name,  the second is any additional documentation that should be added  to the `Abstract<ProcessName>Model` type, and the third determines whether  the short tutorial should be printed or not.

Newcomers are encouraged to use this macro because it explains in detail what to do next with the process. But more experienced users may want to directly define their process without  printing the tutorial. To do so, you can just define a new abstract type and define it as a  subtype of `AbstractModel`:

```julia
abstract type MyNewProcess <: AbstractModel end
```

# Examples

```julia
@process "dummy_process" "This is a dummy process that shall not be used"
```
