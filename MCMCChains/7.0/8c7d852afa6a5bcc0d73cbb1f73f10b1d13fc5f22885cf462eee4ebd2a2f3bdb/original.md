```
hpd(chn::Chains; alpha::Real=0.05, kwargs...)
```

Return the highest posterior density interval representing `1-alpha` probability mass.

Note that this will return a single interval and will not return multiple intervals for discontinuous regions.

# Examples

```julia-repl
julia> val = rand(500, 2, 3);
julia> chn = Chains(val, [:a, :b]);

julia> hpd(chn)
HPD
  parameters     lower     upper 
      Symbol   Float64   Float64 

           a    0.0554    0.9944
           b    0.0114    0.9460
```
