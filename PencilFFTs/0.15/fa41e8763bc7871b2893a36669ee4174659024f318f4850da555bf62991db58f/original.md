```
PencilFFTPlan{T,N} <: AbstractFFTs.Plan{T}
```

Plan for N-dimensional FFT-based transform on MPI-distributed data, where input data has type `T`.

---

```
PencilFFTPlan(p::Pencil, transforms; kwargs...)
```

Create a `PencilFFTPlan` for distributed arrays following a given [`Pencil`](https://jipolanco.github.io/PencilArrays.jl/dev/Pencils/#PencilArrays.Pencils.Pencil) configuration. See variant below for details on the specification of `transforms` and on possible keyword arguments.

---

```
PencilFFTPlan(
    A::PencilArray, transforms;
    fftw_flags = FFTW.ESTIMATE,
    fftw_timelimit = FFTW.NO_TIMELIMIT,
    permute_dims = Val(true),
    transpose_method = Transpositions.PointToPoint(),
    timer = timer(pencil(A)),
)
```

Create plan for `N`-dimensional transform on MPI-distributed `PencilArray`s.

# Extended help

This creates a `PencilFFTPlan` for arrays sharing the same properties as `A` (dimensions, MPI decomposition, memory layout, ...), which describe data on an `N`-dimensional domain.

## Transforms

The transforms to be applied along each dimension are specified by the `transforms` argument. Possible transforms are defined as subtypes of [`Transforms.AbstractTransform`](@ref), and are listed in [Transform types](@ref). This argument may be either:

  * a tuple of `N` transforms to be applied along each dimension. For instance, `transforms = (Transforms.R2R(FFTW.REDFT01), Transforms.RFFT(), Transforms.FFT())`;
  * a single transform to be applied along all dimensions. The input is automatically expanded into `N` equivalent transforms. For instance, for a three-dimensional array, `transforms = Transforms.RFFT()` specifies a 3D real-to-complex transform, and is equivalent to passing `(Transforms.RFFT(), Transforms.FFT(), Transforms.FFT())`.

Note that forward transforms are applied from left to right. In the last example, this means that a real-to-complex transform (`RFFT`) is first performed along the first dimension. This is followed by complex-to-complex transforms (`FFT`) along the second and third dimensions.

## Input data layout

The input `PencilArray` must satisfy the following constraints:

  * array dimensions must *not* be permuted. This is the default when constructing `PencilArray`s.
  * for an `M`-dimensional domain decomposition (with `M < N`), the input array must be decomposed along the *last `M` dimensions*. For example, for a 2D decomposition of 3D data, the decomposed dimensions must be `(2, 3)`. In particular, the first array dimension must *not* be distributed among different MPI processes.

    In the PencilArrays package, the decomposed dimensions are specified at the moment of constructing a [`Pencil`](https://jipolanco.github.io/PencilArrays.jl/dev/Pencils/#PencilArrays.Pencils.Pencil).
  * the element type must be compatible with the specified transform. For instance, real-to-complex transforms (`Transforms.RFFT`) require the input to be real floating point values. Other transforms, such as `Transforms.R2R`, accept both real and complex data.

## Keyword arguments

  * The keyword arguments `fftw_flags` and `fftw_timelimit` are passed to the `FFTW` plan creation functions (see [`AbstractFFTs` docs](https://juliamath.github.io/AbstractFFTs.jl/stable/api/#AbstractFFTs.plan_fft)).
  * `permute_dims` determines whether the indices of the output data should be reversed. For instance, if the input data has global dimensions `(Nx, Ny, Nz)`, then the output of a complex-to-complex FFT would have dimensions `(Nz, Ny, Nx)`. This enables FFTs to always be performed along the first (i.e. fastest) array dimension, which could lead to performance gains. This option is enabled by default. For type inference reasons, it must be a value type (`Val(true)` or `Val(false)`).
  * `transpose_method` allows to select between implementations of the global data transpositions. See [PencilArrays docs](https://jipolanco.github.io/PencilArrays.jl/dev/Transpositions/#PencilArrays.Transpositions.Transposition) docs for details.
  * `timer` should be a `TimerOutput` object. See [Measuring performance](@ref PencilFFTs.measuring_performance) for details.

---

```
PencilFFTPlan(
    dims_global::Dims{N}, transforms, proc_dims::Dims{M}, comm::MPI.Comm,
    [real_type = Float64]; extra_dims = (), kws...
)
```

Create plan for N-dimensional transform.

# Extended help

Instead of taking a `PencilArray` or a `Pencil`, this constructor requires the global dimensions of the input data, passed via the `size_global` argument.

The data is distributed over the MPI processes in the `comm` communicator. The distribution is performed over `M` dimensions (with `M < N`) according to the values in `proc_dims`, which specifies the number of MPI processes to put along each dimension.

`PencilArray`s that may be transformed with the returned plan can be created using [`allocate_input`](@ref).

## Optional arguments

  * The floating point precision can be selected by setting `real_type` parameter, which is `Float64` by default.
  * `extra_dims` may be used to specify the sizes of one or more extra dimensions that should not be transformed. These dimensions will be added to the rightmost (i.e. slowest) indices of the arrays. See **Extra dimensions** below for usage hints.
  * see the other constructor for more keyword arguments.

## Extra dimensions

One possible application of `extra_dims` is for describing the components of a vector or tensor field. However, this means that different `PencilFFTPlan`s would need to be created for each kind of field (scalar, vector, ...). To avoid the creation of multiple plans, a possibly better alternative is to create tuples (or arrays) of `PencilArray`s using [`allocate_input`](@ref) and [`allocate_output`](@ref).

Another more legitimate usage of `extra_dims` is to specify one or more Cartesian dimensions that should not be transformed nor split among MPI processes.

## Example

Suppose we want to perform a 3D FFT of real data. The data is to be decomposed along two dimensions, over 8 MPI processes:

```julia
size_global = (64, 32, 128)  # size of real input data

# Perform real-to-complex transform along the first dimension, then
# complex-to-complex transforms along the other dimensions.
transforms = (Transforms.RFFT(), Transforms.FFT(), Transforms.FFT())
# transforms = Transforms.RFFT()  # this is equivalent to the above line

proc_dims = (4, 2)  # 2D decomposition
comm = MPI.COMM_WORLD

plan = PencilFFTPlan(size_global, transforms, proc_dims, comm)
```
