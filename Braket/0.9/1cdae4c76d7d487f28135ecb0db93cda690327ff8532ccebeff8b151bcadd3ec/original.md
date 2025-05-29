```
depth(c::Circuit)
```

Returns the number of moments in `c`. Also known as the "parallel gate depth".

# Examples

```jldoctest
julia> c = Circuit();

julia> H(c, 0);

julia> CNot(c, 0, 1);

julia> depth(c)
2
```
