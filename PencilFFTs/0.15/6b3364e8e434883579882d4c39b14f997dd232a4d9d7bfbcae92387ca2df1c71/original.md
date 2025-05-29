```
allocate_output(p::PencilFFTPlan)          -> PencilArray
allocate_output(p::PencilFFTPlan, dims...) -> Array{PencilArray}
allocate_output(p::PencilFFTPlan, Val(N))  -> NTuple{N, PencilArray}
```

Allocate uninitialised [`PencilArray`](https://jipolanco.github.io/PencilArrays.jl/dev/PencilArrays/#PencilArrays.PencilArray) that can hold output data for the given plan.

If `p` is an in-place plan, a [`ManyPencilArray`](https://jipolanco.github.io/PencilArrays.jl/dev/PencilArrays/#PencilArrays.ManyPencilArray) is allocated.

See [`allocate_input`](@ref) for details.
