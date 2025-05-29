```
on(f, observable::AbstractObservable; weak = false, priority=0, update=false)::ObserverFunction
```

Adds function `f` as listener to `observable`. Whenever `observable`'s value is set via `observable[] = val`, `f` is called with `val`.

Returns an [`ObserverFunction`](@ref) that wraps `f` and `observable` and allows to disconnect easily by calling `off(observerfunction)` instead of `off(f, observable)`. If instead you want to compute a new `Observable` from an old one, use [`map(f, ::Observable)`](@ref).

If `weak = true` is set, the new connection will be removed as soon as the returned `ObserverFunction` is not referenced anywhere and is garbage collected. This is useful if some parent object makes connections to outside observables and stores the resulting `ObserverFunction` instances. Then, once that parent object is garbage collected, the weak observable connections are removed automatically.

# Example

```julia
julia> obs = Observable(0)
Observable(0)

julia> on(obs) do val
           println("current value is ", val)
       end
ObserverFunction defined at REPL[17]:2 operating on Observable(0)
julia> obs[] = 5;
current value is 5
```

One can also give the callback a priority, to enable always calling a specific callback before/after others, independent of the order of registration. The callback with the highest priority gets called first, the default is zero, and the whole range of Int can be used. So one can do:

```julia
julia> obs = Observable(0)
julia> on(obs; priority=-1) do x
           println("Hi from first added")
       end
julia> on(obs) do x
           println("Hi from second added")
       end
julia> obs[] = 2
Hi from second added
Hi from first added
```

If you set `update=true`, on will call f(obs[]) immediately:

```julia
julia> on(Observable(1); update=true) do x
    println("hi")
end
hi
```
