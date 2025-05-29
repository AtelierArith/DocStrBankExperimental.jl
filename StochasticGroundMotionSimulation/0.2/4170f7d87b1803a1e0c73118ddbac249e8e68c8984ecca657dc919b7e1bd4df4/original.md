```
magnitude_to_moment(m::T) where T<:Real
```

Converts moment magnitude to seismic moment (in dyne-cm).

# Examples

```julia-repl
	m = 6.0
	M0 = magnitude_to_moment(m)
```
