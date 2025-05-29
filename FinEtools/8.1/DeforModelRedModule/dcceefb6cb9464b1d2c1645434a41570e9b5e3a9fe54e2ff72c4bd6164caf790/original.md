```
stresscomponentmap(::Type{DeforModelRed1D})
```

Construct a dictionary to map from stress-component symbols to indexes.

# Example

Which component of the stress vector is for instance sigma_x? Do

```
julia> comp = stresscomponentmap(DeforModelRed1D)
Dict{Symbol,Int64} with 2 entries:
  :xx => 1
  :x  => 1

julia>

julia> comp[:x]
1
```
