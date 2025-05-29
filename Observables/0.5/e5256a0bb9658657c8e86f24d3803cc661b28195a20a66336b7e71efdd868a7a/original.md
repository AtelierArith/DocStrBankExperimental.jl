```
obs = map(f, arg1::AbstractObservable, args...; ignore_equal_values=false)
```

Creates a new observable `obs` which contains the result of `f` applied to values extracted from `arg1` and `args` (i.e., `f(arg1[], ...)`. `arg1` must be an observable for dispatch reasons. `args` may contain any number of `Observable` objects. `f` will be passed the values contained in the observables as the respective argument. All other objects in `args` are passed as-is.

If you don't need the value of `obs`, and just want to run `f` whenever the arguments update, use [`on`](@ref) or [`onany`](@ref) instead.

# Example

```jldoctest; setup=:(using Observables)
julia> obs = Observable([1,2,3]);

julia> map(length, obs)
Observable(3)
```
