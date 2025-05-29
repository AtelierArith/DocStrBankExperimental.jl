```
copy!(xf::Transducer, dest, src)
```

Feed `src` to transducer `xf`, storing the result in `dest`. Collections `dest` and `src` may have the same shape.  Source `src` must be iterable.  Destination `dest` must implement `empty!` and `push!`.

See also [`map!`](@ref).

# Examples

```jldoctest
julia> using Transducers

julia> copy!(opcompose(PartitionBy(x -> x ÷ 3), Map(sum)), Int[], 1:10)
4-element Vector{Int64}:
  3
 12
 21
 19
```
