```
SeisDelay(in; <keyword arguments>)
```

Apply a time delay to 2D data

# Arguments

  * `in`: input 2D data array in tx domain. First dimension is time.

# Keyword arguments

  * `delay=0.1`: desired time delay in secs.
  * `dt=0.004`: time sampling interval in secs.

# Example

```julia
julia> d = SeisLinearEvents(); deli = SeisDelay(d);
```

*Credits: Aaron Stanton,2017*
