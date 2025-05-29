```
magref(cmd0::String="", arg1=nothing; kwargs...)
```

Evaluate the IGRF or CM4 magnetic field models.

To see the full documentation type: $@? magref$

### Example

```julia
	G = magref(R=:d, onetime=2020);
	viz(G, coast=true)
```
