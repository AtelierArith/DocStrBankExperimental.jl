```
Pencil{N,M}
```

Describes the decomposition of an `N`-dimensional array among MPI processes along `M` directions (with `M < N`).

---

```
Pencil(
    [A = Array],
    topology::MPITopology{M}, size_global::Dims{N},
    decomp_dims::Dims{M} = default_decomposition(N, Val(M));
    permute::AbstractPermutation = NoPermutation(),
    timer = TimerOutput(),
)
```

Define the decomposition of an `N`-dimensional geometry along `M` dimensions.

The dimensions of the geometry are given by `size_global = (N1, N2, ...)`. The `Pencil` describes the decomposition of an array of dimensions `size_global` across a group of MPI processes.

Data is distributed over the given `M`-dimensional MPI topology (with `M ≤ N`).

The decomposed dimensions may optionally be provided via the `decomp_dims` argument. By default, the `M` rightmost dimensions are decomposed. For instance, for a 2D decomposition of 5D data (`M = 2` and `N = 5`), the dimensions `(4, 5)` are decomposed by default.

It is also possible to distribute over all dimensions (`M = N`). Note that, in this specific case, [transpositions](@ref Global-MPI-operations) are currently not possible.

The optional argument `A` allows to work with arrays other than the base `Array` type. In particular, this should be useful for working with GPU array types such as `CuArray`.

The optional `permute` parameter may be used to indicate a permutation of the data indices from **logical order** (the order in which the arrays are accessed in code) to **memory order** (the actual order of indices in memory). Permutations must be specified using the exported `Permutation` type, as in `permute = Permutation(3, 1, 2)`.

It is also possible to pass a `TimerOutput` to the constructor. See [Measuring performance](@ref PencilArrays.measuring_performance) for details.

# Examples

Decompose a 3D geometry of global dimensions $N_x × N_y × N_z = 4×8×12$ along the second ($y$) and third ($z$) dimensions:

```jldoctest
julia> topo = MPITopology(MPI.COMM_WORLD, Val(2));

julia> Pencil(topo, (4, 8, 12), (2, 3))
Decomposition of 3D data
    Data dimensions: (4, 8, 12)
    Decomposed dimensions: (2, 3)
    Data permutation: NoPermutation()
    Array type: Array

julia> Pencil(topo, (4, 8, 12), (2, 3); permute = Permutation(3, 2, 1))
Decomposition of 3D data
    Data dimensions: (4, 8, 12)
    Decomposed dimensions: (2, 3)
    Data permutation: Permutation(3, 2, 1)
    Array type: Array

```

In the second case, the actual data is stored in `(z, y, x)` order within each MPI process.

---

```
Pencil([A = Array], size_global::Dims{N}, [decomp_dims = (2, …, N)], comm::MPI.Comm; kws...)
```

Convenience constructor that implicitly creates a [`MPITopology`](@ref).

The number of decomposed dimensions specified by `decomp_dims` must be `M < N`. If `decomp_dims` is not passed, dimensions `2:N` are decomposed.

Keyword arguments are passed to alternative constructor taking an `MPITopology`. That constructor should be used if more control is desired.

# Examples

```jldoctest
julia> Pencil((4, 8, 12), MPI.COMM_WORLD)
Decomposition of 3D data
    Data dimensions: (4, 8, 12)
    Decomposed dimensions: (2, 3)
    Data permutation: NoPermutation()
    Array type: Array

julia> Pencil((4, 8, 12), (1, ), MPI.COMM_WORLD)
Decomposition of 3D data
    Data dimensions: (4, 8, 12)
    Decomposed dimensions: (1,)
    Data permutation: NoPermutation()
    Array type: Array
```

---

```
Pencil(
    [A = Array],
    p::Pencil{N,M};
    decomp_dims::Dims{M} = decomposition(p),
    size_global::Dims{N} = size_global(p),
    permute::P = permutation(p),
    timer::TimerOutput = timer(p),
)
```

Create new pencil configuration from an existent one.

This constructor enables sharing temporary data buffers between the two pencil configurations, leading to reduced global memory usage.
