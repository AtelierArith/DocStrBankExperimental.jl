```
split(s::SeisBlock, inds::Union{Vector{Ti}, AbstractRange{Ti}};
           consume::Bool = false) where {Ti<:Integer}
```

Split the 'ind' traces of `s` into a sepretate `SeisBlock` object.

The default behaviour does not change the input object `s`. The returned `SeisBlock` is  created by referencing the traceheaders of `s`, and copying the subset of the data.

If memory use is a concern, the `consume` keyword changes the behaviour of `merge`. If `consume` is true, then the `ind` traces of `s` are REMOVED and placed into the returned `SeisBlock` object. In this case, `merge` will operate in place on `s`, while still returning a  subset of `s`.

# Examples

```
julia> using SegyIO

julia> s = segy_scan(joinpath(dirname(pathof(SegyIO)),"data/"), "overthrust", ["GroupX"; "GroupY"], verbosity = 0);

julia> d = s[1:length(s)]; @time b = split(d, 1:10000);
  0.005683 seconds (23 allocations: 28.649 MiB, 17.99% gc time)

julia> println("d: ", size(d)); println("b: ", size(b))
d: (751, 20013)
b: (751, 10000)

julia> data_in_memory = Base.summarysize(d.data) + Base.summarysize(b.data)
90159052
```

Note that the default behaviour of `merge` is to create `b` by copying `d`.

```
julia> d = s[1:length(s)]; @time b = split(d, 1:10000, consume=true);
  0.062364 seconds (37 allocations: 116.537 MiB, 19.44% gc time)

julia> println("d: ", size(d)); println("b: ", size(b))
d: (751, 10013)
b: (751, 10000)

julia> data_in_memory = Base.summarysize(d.data) + Base.summarysize(b.data)
60119052
```

In this case, because `consume` was set to true, `merge` created `b` by removing traces from `d`. `consume` prevents the duplication of data in memory at the cost of performance, memory allocation, and risk.
