```
allocate_input(p::PencilFFTPlan)          -> PencilArray
allocate_input(p::PencilFFTPlan, dims...) -> Array{PencilArray}
allocate_input(p::PencilFFTPlan, Val(N))  -> NTuple{N, PencilArray}
```

Allocate uninitialised [`PencilArray`](https://jipolanco.github.io/PencilArrays.jl/dev/PencilArrays/#PencilArrays.PencilArray) that can hold input data for the given plan.

The second and third forms respectively allocate an array of `PencilArray`s of size `dims`, and a tuple of `N` `PencilArray`s.

!!! note "In-place plans"
    If `p` is an in-place real-to-real or complex-to-complex plan, a [`ManyPencilArray`](https://jipolanco.github.io/PencilArrays.jl/dev/PencilArrays/#PencilArrays.ManyPencilArray) is allocated. If `p` is an in-place real-to-complex plan, a [`ManyPencilArrayRFFT!`](@ref) is allocated. 

    These types hold `PencilArray` wrappers for the input and output transforms (as well as for intermediate transforms) which share the same space in memory. The input and output `PencilArray`s should be respectively accessed by calling [`first(::ManyPencilArray)`](https://jipolanco.github.io/PencilArrays.jl/dev/PencilArrays/#Base.first-Tuple{ManyPencilArray}) and [`last(::ManyPencilArray)`](https://jipolanco.github.io/PencilArrays.jl/dev/PencilArrays/#Base.last-Tuple{ManyPencilArray}).

    #### Example

    Suppose `p` is an in-place `PencilFFTPlan`. Then,

    ```julia
    @assert is_inplace(p)
    A = allocate_input(p) :: ManyPencilArray
    v_in = first(A)       :: PencilArray  # input data view
    v_out = last(A)       :: PencilArray  # output data view
    ```

    Also note that in-place plans must be performed directly on the returned `ManyPencilArray`, and not on the contained `PencilArray` views:

    ```julia
    p * A       # perform forward transform in-place
    p \ A       # perform backward transform in-place
    # p * v_in  # not allowed!!
    ```

