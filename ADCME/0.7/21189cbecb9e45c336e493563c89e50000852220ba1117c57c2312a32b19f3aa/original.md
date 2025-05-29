```
pad(o::PyObject, paddings::Array{Int64, 2}, args...; kwargs...)
```

Pads `o` with values on the boundary. 

# Example

```julia
o = rand(3,3)
o = pad(o, [1 4      # first dimension
             2 3])   # second dimension
run(sess, o)
```

Expected:

```
8×8 Array{Float64,2}:
 0.0  0.0  0.0       0.0       0.0       0.0  0.0  0.0
 0.0  0.0  0.250457  0.666905  0.823611  0.0  0.0  0.0
 0.0  0.0  0.23456   0.625145  0.646713  0.0  0.0  0.0
 0.0  0.0  0.552415  0.226417  0.67802   0.0  0.0  0.0
 0.0  0.0  0.0       0.0       0.0       0.0  0.0  0.0
 0.0  0.0  0.0       0.0       0.0       0.0  0.0  0.0
 0.0  0.0  0.0       0.0       0.0       0.0  0.0  0.0
 0.0  0.0  0.0       0.0       0.0       0.0  0.0  0.0
```
