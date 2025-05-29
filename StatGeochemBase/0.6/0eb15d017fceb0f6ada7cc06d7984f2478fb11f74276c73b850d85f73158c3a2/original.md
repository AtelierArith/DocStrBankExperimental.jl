```julia
leastsigfig(d)
```

Return the order of magnitude of the least significant decimal digit of a number `d`.

### Examples

```julia
julia> leastsigfig(1000)
1000.0

julia> leastsigfig(1001)
1.0

julia> leastsigfig(1001.1234)
0.0001
```
