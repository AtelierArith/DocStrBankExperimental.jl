```
hcubature_buffer(f,a,b;norm=norm)
```

Allocate a buffer that can be used in calls to [`hcubature`](@ref). The arguments `(f,a,b;norm)` are the same as those passed to [`hcubature`](@ref).

The resulting buffer can be re-used with different *values* of `a,b` and `f` as long as, the *type* of the enpoints `a,b` remains the same, and the *return type* of `f` does not change.

Pre-allocating a buffer is only useful if you're going to be calling `hcubature` several times on *similar* arguments `f,a,b`, and if the cost of buffer allocation (and/or the associated garbage collection) is significant compared to the actual evaluation of the integral.

# Examples:

```julia
f = x -> cos(x[1])*cos(x[2])
a,b = (0,0), (1,1)
buffer = hcubature_buffer(f,a,b)
I,E = hcubature(f,a,b; buffer=buffer)

# the buffer can be re-used on similar calls
g = x -> sin(x[1])*sin(x[2])
a,b = (0,0), (1.5,1.5)
I,E = hcubature(g,a,b; buffer=buffer)
```
