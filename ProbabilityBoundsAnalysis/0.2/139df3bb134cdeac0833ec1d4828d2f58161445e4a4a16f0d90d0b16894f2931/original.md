```
imp(x :: pbox, y :: pbox)
```

Imprint. Returns the intersection of pboxes

# Examples

```jldoctest
julia> a = U(interval(0, 1), 2);

julia> b = U(1, 2);

julia> c = imp(a, b)
Pbox: 	  ~  ( range=[1.0, 2.0], mean=1.5, var=0.083333)
```

See also: [`env`](@ref), [`makepbox`](@ref)
