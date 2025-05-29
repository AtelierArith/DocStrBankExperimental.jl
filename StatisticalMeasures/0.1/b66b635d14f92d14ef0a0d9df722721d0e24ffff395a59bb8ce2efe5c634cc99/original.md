```
measures(needle::Union{AbstractString,Regex}; trait_options...)
```

*Experimental* and subject to breaking behavior between patch releases.

Find measures that contain `needle` in their document string.  Returns a dictionary keyed on the constructors of such measures.

```
julia> measures("Matthew")
LittleDict{Any, Any, Vector{Any}, Vector{Any}} with 1 entry:
  MatthewsCorrelation => (aliases = ("matthews_correlation", "mcc"), consumes_multiple_obse…
```
