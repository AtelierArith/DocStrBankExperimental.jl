```
generate_level_parts(root_parts::AbstractArray,num_procs_x_level::Vector{<:Integer})
```

From a root communicator `root_parts`, generate a sequence of nested    subcommunicators with sizes given by `num_procs_x_level`.
