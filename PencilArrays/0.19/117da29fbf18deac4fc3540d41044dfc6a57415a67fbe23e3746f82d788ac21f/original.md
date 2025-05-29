```
PencilArray(pencil::Pencil, data::AbstractArray{T,N})
```

Create array wrapper with pencil decomposition information.

The array dimensions and element type must be consistent with those of the given pencil.

!!! note "Index permutations"
    If the `Pencil` has an associated index permutation, then `data` must have its dimensions permuted accordingly (in *memory* order).

    Unlike `data`, the resulting `PencilArray` should be accessed with unpermuted indices (in *logical* order).

    ##### Example

    Suppose `pencil` has local dimensions `(10, 20, 30)` before permutation, and has an asociated permutation `(2, 3, 1)`. Then:

    ```julia
    data = zeros(20, 30, 10)       # parent array (with dimensions in memory order)

    u = PencilArray(pencil, data)  # wrapper with dimensions (10, 20, 30)
    @assert size_local(u) === (10, 20, 30)

    u[15, 25, 5]          # BoundsError (15 > 10 and 25 > 20)
    u[5, 15, 25]          # correct
    parent(u)[15, 25, 5]  # correct

    ```


!!! note "Extra dimensions"
    The data array can have one or more extra dimensions to the right (slow indices), which are not affected by index permutations.

    ##### Example

    ```julia
    dims = (20, 30, 10)
    PencilArray(pencil, zeros(dims...))        # works (scalar)
    PencilArray(pencil, zeros(dims..., 3))     # works (3-component vector)
    PencilArray(pencil, zeros(dims..., 4, 3))  # works (4×3 tensor)
    PencilArray(pencil, zeros(3, dims...))     # fails
    ```


---

```
PencilArray{T}(undef, pencil::Pencil, [extra_dims...])
```

Allocate an uninitialised `PencilArray` that can hold data in the local pencil.

Extra dimensions, for instance representing vector components, can be specified. These dimensions are added to the rightmost (slowest) indices of the resulting array.

# Example

Suppose `pencil` has local dimensions `(20, 10, 30)`. Then:

```julia
PencilArray{Float64}(undef, pencil)        # array dimensions are (20, 10, 30)
PencilArray{Float64}(undef, pencil, 4, 3)  # array dimensions are (20, 10, 30, 4, 3)
```

More examples:

```jldoctest
julia> pen = Pencil((20, 10, 12), MPI.COMM_WORLD);

julia> u = PencilArray{Float64}(undef, pen);

julia> summary(u)
"20×10×12 PencilArray{Float64, 3}(::Pencil{3, 2, NoPermutation, Array})"

julia> PencilArray{Float64}(undef, pen, 4, 3) |> summary
"20×10×12×4×3 PencilArray{Float64, 5}(::Pencil{3, 2, NoPermutation, Array})"

```
