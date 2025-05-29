```julia
struct BVHOptions{I<:Integer, T}
```

Options for building and traversing bounding volume hierarchies, including parallel strategy settings.

An exemplar of an index (e.g. `Int32(0)`) is used to deduce the types of indices used in the BVH building ([`ImplicitTree`](@ref), order) and traversal ([`IndexPair`](@ref)).

The CPU scheduler can be `:threads` (for base Julia threads) or `:polyester` (for Polyester.jl threads).

If `compute_extrema=false` and `mins` / `maxs` are defined, they will not be computed from the distribution of bounding volumes; useful if you have a fixed simulation box, for example. You **must** ensure that no bounding volume centers will touch or be outside these bounds, otherwise logically incorrect results will be silently produced.

# Methods

```
BVHOptions(;

    # Example index from which to deduce type
    index_exemplar::I               = Int32(0),

    # CPU threading
    scheduler::Symbol               = :threads,
    num_threads::Int                = Threads.nthreads(),
    min_mortons_per_thread::Int     = 1000,
    min_boundings_per_thread::Int   = 1000,
    min_traversals_per_thread::Int  = 1000,

    # GPU scheduling
    block_size::Int                 = 256,

    # Minima / maxima
    compute_extrema::Bool           = true,
    mins::NTuple{3, T}              = (NaN32, NaN32, NaN32),
    maxs::NTuple{3, T}              = (NaN32, NaN32, NaN32),
) where {I <: Integer, T}
```

# Fields

  * `index_exemplar::Integer`
  * `scheduler::Symbol`
  * `num_threads::Int64`
  * `min_mortons_per_thread::Int64`
  * `min_boundings_per_thread::Int64`
  * `min_traversals_per_thread::Int64`
  * `block_size::Int64`
  * `compute_extrema::Bool`
  * `mins::Tuple{T, T, T} where T`
  * `maxs::Tuple{T, T, T} where T`
