```
@set name = value
```

This can be used inside a `@tasks for ... end` block to specify settings for the parallel execution of the loop.

Multiple settings are supported, either as separate `@set` statements or via `@set begin ... end`.

## Settings

  * `reducer` (e.g. `reducer=+`): Indicates that a reduction should be performed with the provided binary function. See [`tmapreduce`](@ref) for more information.
  * `collect` (e.g. `collect=true`): Indicates that results should be collected (similar to `map`).

All other settings will be passed on to the underlying parallel functions (e.g. [tmapreduce](@ref)) as keyword arguments. Hence, you may provide whatever these functions accept as keyword arguments. Among others, this includes

  * `scheduler` (e.g. `scheduler=:static`): Can be either a [`Scheduler`](@ref) or a `Symbol` (e.g. `:dynamic`, `:static`, `:serial`, or `:greedy`).
  * `init` (e.g. `init=0.0`): Initial value to be used in a reduction (requires `reducer=...`).

Settings like `ntasks`, `chunksize`, and `split` etc. can be used to tune the scheduling policy (if the selected scheduler supports it).

Note that the assignment is hoisted above the loop body which means that the scope is *not* the scope of the loop (even though it looks like it) but rather the scope *surrounding* the loop body. (`@macroexpand` is a useful tool to inspect the generated code of the `@tasks` block.)
