```
on(f, observable::AbstractObservable; weak = false)
```

Adds function `f` as listener to `observable`. Whenever `observable`'s value is set via `observable[] = val`, `f` is called with `val`.

Returns an [`ObserverFunction`](@ref) that wraps `f` and `observable` and allows to disconnect easily by calling `off(observerfunction)` instead of `off(f, observable)`. If instead you want to compute a new `Observable` from an old one, use [`map(f, ::Observable)`](@ref).

If `weak = true` is set, the new connection will be removed as soon as the returned `ObserverFunction` is not referenced anywhere and is garbage collected. This is useful if some parent object makes connections to outside observables and stores the resulting `ObserverFunction` instances. Then, once that parent object is garbage collected, the weak observable connections are removed automatically.

# Example

```jldoctest; setup=:(using Observables)
julia> obs = Observable(0)
Observable{Int64} with 0 listeners. Value:
0

julia> on(obs) do val
           println("current value is ", val)
       end
(::Observables.ObserverFunction) (generic function with 0 methods)

julia> obs[] = 5;
current value is 5
```
