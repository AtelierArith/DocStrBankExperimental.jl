```
merge(a::SeisBlock{DT}, b::SeisBlock{DT};
           force::Bool = false, consume::Bool = false) where {DT<:Union{IBMFloat32, Float32}}
```

Merge `blocks`, a vector of `SeisBlock` objects into one `SeisBlock` object.

By default, `merge` checks to ensure that each `SeisBlock` has matching fileheaders. This ensures that the returned `SeisBlock` is consistant with it's fileheader. This check can be turned off using the `force` keyword. If set to false, `merge` will attempt to combine `blocks` without checking fileheader metadata. The first fileheader in `blocks` will be used for the  returned  `SeisBlock`'s fileheader. 

By default, `merge` references traceheaders, but copies data from the elements of `blocks`.  If memory use is a concern, the `consume` keyword will clear the traceheader and data field of each  element of `block` after it has been copied. This will prevent duplicating the data in memory, at the cost of clearing the elements of `blocks`.

# Examples

```
julia> s = segy_scan(joinpath(dirname(pathof(SegyIO)),"data/"), "overthrust", ["GroupX"; "GroupY"], verbosity = 0);

julia> a = s[1:4]; b = s[5:8];

julia> c = merge([a; b]);

julia> c.traceheaders[1] === a.traceheaders[1]
true

julia> c = merge([a; b], consume = true);

julia> a.traceheaders
0-element Array{SegyIO.BinaryTraceHeader,1}
```
