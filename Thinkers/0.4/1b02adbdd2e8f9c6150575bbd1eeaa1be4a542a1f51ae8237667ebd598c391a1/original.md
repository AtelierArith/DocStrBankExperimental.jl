```
Thunk(callable, args...; kwargs...)
```

Hold a callable and its arguments for lazy evaluation. Use `reify!` to evaluate.

# Examples

```jldoctest
julia> using Thinkers

julia> a = Thunk(x -> 3x, 4);

julia> reify!(a);

julia> getresult(a)
Some(12)

julia> b = Thunk(+, 4, 5);

julia> reify!(b);

julia> getresult(b)
Some(9)

julia> c = Thunk(sleep, 1);

julia> getresult(c)  # `c` has not been evaluated

julia> reify!(c);  # `c` has been evaluated

julia> getresult(c)
Some(nothing)

julia> f(args...; kwargs...) = collect(kwargs);

julia> d = Thunk(f, 1, 2, 3; x=1.0, y=4, z="5");

julia> reify!(d);

julia> getresult(d)
Some(Pair{Symbol, Any}[:x => 1.0, :y => 4, :z => "5"])

julia> e = Thunk(sin, "1");  # Catch errors

julia> reify!(e);

julia> haserred(e)
true
```
