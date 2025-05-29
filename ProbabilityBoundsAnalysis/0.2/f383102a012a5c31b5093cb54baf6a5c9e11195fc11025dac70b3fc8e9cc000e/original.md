```
env(x :: pbox, y :: pbox)
```

Envelope. Returns the union of pboxes.

# Examples

```jldoctest
julia> a = U(0,1);

julia> b = U(1,2);

julia> c = env(a, b)
Pbox: 	  ~ uniform ( range=[0.0, 2.0], mean=[0.5, 1.5], var=0.083333)
```

See also: [`imp`](@ref), [`makepbox`](@ref)
