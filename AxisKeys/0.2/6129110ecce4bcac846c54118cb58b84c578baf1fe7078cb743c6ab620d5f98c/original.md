```
wrapdims(A, :i, :j)
wrapdims(A, 1:10, ['a', 'b', 'c'])
wrapdims(A, i=1:10, j=['a', 'b', 'c'])
```

Convenience function for constructing either a `NamedDimsArray`, a `KeyedArray`, or a nested pair of both.

Performs some sanity checks which are skipped by `KeyedArray` constructor:

  * Giving `nothing` instead of keys will result in `axiskeys(A,d) == axes(A,d)`.
  * Given an `AbstractRange` of the wrong length, it will adjust the end of this, and give a warning.
  * Given `A::OffsetArray` and key vectors which are not, it will wrap them so that `axes.(axiskeys(A_wrapped)) == axes(A)`.

By default it wraps in this order: `KeyedArray{...,NamedDimsArray{...}}`, which you can change by re-defining `AxisKeys.nameouter() == true`.

# Examples

```jldoctest
julia> wrapdims([1,10,100], pow=0:99)
┌ Warning: range 0:99 replaced by 0:2, to match size(A, 1) == 3
└ @ AxisKeys ~/.julia/dev/AxisKeys/src/wrap.jl:50
1-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   pow ∈ 3-element UnitRange{Int64}
And data, 3-element Vector{Int64}:
 (0)    1
 (1)   10
 (2)  100

julia> push!(ans, 1000)
1-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   pow ∈ 4-element UnitRange{Int64}
And data, 4-element Vector{Int64}:
 (0)     1
 (1)    10
 (2)   100
 (3)  1000
```
