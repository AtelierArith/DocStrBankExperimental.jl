```
while_loop(condition::Union{PyObject,Function}, body::Function, loop_vars::Union{PyObject, Array{Any}, Array{PyObject}};
    parallel_iterations::Int64=10, kwargs...)
```

Loops over `loop_vars` while `condition` is true. This operator only creates one extra node to mark the loops in the computational graph.

# Example

The following script computes 

$$
\sum_{i=1}^{10} i
$$

```julia
function condition(i, ta)
    i <= 10
end
function body(i, ta)
    u = read(ta, i-1)
    ta = write(ta, i, u+1)
    i+1, ta
end
ta = TensorArray(10)
ta = write(ta, 1, constant(1.0))
i = constant(2, dtype=Int32)
_, out = while_loop(condition, body, [i, ta])
summation = stack(out)[10]
```
