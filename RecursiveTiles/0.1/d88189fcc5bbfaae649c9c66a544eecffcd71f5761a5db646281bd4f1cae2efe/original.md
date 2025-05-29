```
Scheme(f, [g=nothing])
```

Functor comprised of `f`, the transformation applied to construct each element of a tile, and `g`, the transformation applied to construct the index of tile. It may be called directly, as shown below, but is most commonly passed to `tile` or `tiles` (perhaps after being wrapped in one or more `ExtendScheme`s).

See also: [`ExtendScheme`](@ref), [`@scheme`](@ref)

# Examples

```jldoctest
julia> s = Scheme(sum, last);

julia> s([1, 2, 3])
(6, 3)

julia> Scheme(sum)([1, 2, 3])
6
```
