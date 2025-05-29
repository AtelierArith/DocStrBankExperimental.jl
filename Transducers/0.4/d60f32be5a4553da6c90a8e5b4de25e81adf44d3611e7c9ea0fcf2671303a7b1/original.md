```
copy(xf::Transducer, T, foldable) :: Union{T, Empty{T}}
copy(xf::Transducer, foldable::T) :: Union{T, Empty{T}}
copy([T,] eduction::Eduction) :: Union{T, Empty{T}}
```

Process `foldable` with a transducer `xf` and then create a container of type `T` filled with the result.  Return [`BangBang.Empty{T}`](https://juliafolds.github.io/BangBang.jl/dev/#BangBang.NoBang.Empty) if the transducer does not produce anything.  (This is because there is no consistent interface to create an empty container given its type and not all containers support creating an empty container.)

For parallel versions, see [`tcopy`](@ref) and [`dcopy`](@ref).

!!! compat "Transducers.jl 0.4.4"
    New in version 0.4.4.


!!! compat "Transducers.jl 0.4.8"
    `copy` now accepts eductions.


# Examples

```jldoctest
julia> using Transducers
       using BangBang: Empty

julia> copy(Map(x -> x => x^2), Dict, 2:2)
Dict{Int64, Int64} with 1 entry:
  2 => 4

julia> @assert copy(Filter(_ -> false), Set, 1:1) === Empty(Set)

julia> using TypedTables

julia> @assert copy(Map(x -> (a=x, b=x^2)), Table, 1:1) == Table(a=[1], b=[1])

julia> using StructArrays

julia> @assert copy(Map(x -> (a=x, b=x^2)), StructVector, 1:1) == StructVector(a=[1], b=[1])

julia> using DataFrames

julia> @assert copy(
           Map(x -> (A = x.a + 1, B = x.b + 1)),
           DataFrame(a = [1], b = [2]),
       ) == DataFrame(A = [2], B = [3])
```
