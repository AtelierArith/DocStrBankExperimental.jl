```
apply(f::Function, patches::Pair...)
```

Run function `f` with the specified `patches` applied. Note that the patches are only effective when the global switch is activated. See also [`Pretend.activate`](@ref).

Each patch in the `patches` argument is a pair of the original function and the patch function. If the patch functtion returns the singleton object `Fallback()` then the original function will be executed.  This provides an easy mechanism of implementing conditional patches.

# Example

```jldoctest
julia> @mockable add(x, y) = x + y;

julia> apply(add => (x,y) -> x - y) do
           @show add(1, 2)
       end;
add(1, 2) = -1

julia> apply(add => (x,y) -> x == y ? 0 : Fallback()) do
           @show add(1, 2)
           @show add(5, 5)
       end;
add(1, 2) = 3
add(5, 5) = 0
```
