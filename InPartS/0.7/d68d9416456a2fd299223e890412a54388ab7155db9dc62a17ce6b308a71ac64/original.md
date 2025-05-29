```
LineageCoordRegistrar{N, T<:Integer} <: AbstractSeqRegistrar{T}
```

Constructors:

```
LineageCoordRegistrar{N, T = UInt64}()
LineageCoordRegistrar(next_id::T = UInt64(1); ndims::Integer, kwargs...)
```

In addition to returning sequential numbers of type `T` (defaults to `UInt64`), this implementation of [`AbstractSeqRegistrar`](@ref) also can keep track of lineages using a dictionary called `parent` and the time and position at which the particle was added. Particles are assumed to have a `centerpos` property of type `SVector{N, Float64}`. `ndims` is another way of specifying `N`. The last two constructors also allow prefilling `parent`, `centerpos` and `times` properties via keyword args.

Calling [`set_id!`](@ref)/[`get_id!`](@ref) on this registrar automatically records the above data.

Example:

```
# Default-intialized registrar for a two-dimensional simulation
reg = LineageCoordRegistrar(ndims=2)

# Same but with type parameter
reg = LineageCoordRegistrar{2}()
```
