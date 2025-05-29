```julia
draw_from_distribution!(x::DenseArray{<:AbstractFloat}, dist::Collection{AbstractFloat})
```

Fill an existing variable `x` with random floating point numbers drawn from a continuous probability distribution specified by a vector `dist` defining the PDF curve thereof.
