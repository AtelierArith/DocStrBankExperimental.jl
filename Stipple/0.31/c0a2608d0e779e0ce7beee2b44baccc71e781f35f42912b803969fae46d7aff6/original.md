```
synchronize!(o1::AbstractObservable, o2::AbstractObservable; priority::Union{Int,Nothing} = nothing, update = true, biderectional = false)
```

Synchronize two observables by setting the value of `o1` to the value of `o2`. Other than `connect!()` this function works bidirectional without creating a loop back. Synchronizing multiple observables is possible, but care should be taken to always synchronize to the same root observable.

### parameters

  * `o1::AbstractObservable`: The first observable to synchronize.
  * `o2::AbstractObservable`: The observable to synchronize with
  * `priority::Union{Int,Nothing}`: The priority of the synchronization listeners.

    The priority is used as identifier of a synchronization pair.   If more than one observables is synchronized they should have different priorities.   If `nothing` (default), search for a unique priority so that the order of synchronization is identical to    the order of synchronize!() calls.
  * `update::Bool`: If `true` then `o1` will be updated with the value of `o2`, default: `true`
  * `biderectional`: If `true` (default) perform two-way synchronization, if `false` sync o1 to follow o2.   The latter functionally identical to `connect!()`, however `unsynchronize!()` only works correctly on    variables synced with `synchronize!()`

### Example 1

```
o = Observable(0)
on(o -> println("o: $o"), o)

o1 = Observable(1)
on(o1 -> println("o1: $o1"), o)

o2 = Observable(2)
on(o2 -> println("o2: $o2"), o)

synchronize!(o1, o)
synchronize!(o2, o)

o[] = 10;
# o: 10
# o1: 10
# o2: 10

o1[] = 11;
# o: 11
# o1: 11
# o2: 11

o2[] = 12;
# o: 12
# o1: 12
# o2: 12
```

### Example 2

```
using Stipple, Stipple.ReactiveTools
using StippleUI

const X = Observable(0)

@app Observer begin
    @in x = 0

    @onchange isready begin
        synchronize!(__model__.x, X)
    end
end

@event Observer :finalize begin
    println("unsynchronizing ...")
    @info unsynchronize!(__model__.x)
    notify(__model__, Val(:finalize))
end

@page("/", slider(1:100, :x), model = Observer)

@debounce Observer x 0
@throttle Observer x 10

up()
```

### Example 3

Modification of Example 2 to sync only tabs with the same session id (i.e. the same browser).

```
using Stipple, Stipple.ReactiveTools
using StippleUI
using GenieSession

const XX = Dict{String, Reactive}()

@app Observer begin
    @in x = 0
    @private session = ""

    @onchange isready begin
        r = get!(XX, session, R(x))
        synchronize!(__model__.x, r)
    end
end

@page("/", slider(1:100, :x), model = Observer, post = model -> begin model.session[] = session().id; nothing end)

@event Observer :finalize begin
    println("unsynchronizing ...")
    @info unsynchronize!(__model__.x)
    notify(__model__, Val(:finalize))
end

@debounce Observer x 0
@throttle Observer x 10

up()
```

Note that `post` has been used to attach the session id to the model. Make sure that the attached function returns nothing in order to proceed with the page rendering. If `post` returns a value, the page will render that value instead of the page content. For further information see [`@page`](@ref).

Unsynchronization via the event :finalize is important to suppress syncing to models that have been replaced by page reloading or navigation.
