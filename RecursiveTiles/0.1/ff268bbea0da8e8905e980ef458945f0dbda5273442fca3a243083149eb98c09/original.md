```
tile(s::AbstractScheme, A)
tile(s::AbstractExtendScheme, A)
```

Construct a `Tile` by applying the scheme, `s`, to the entirety of `A`.

The distinction between `AbstractScheme` and `AbstractExtendScheme` exists for signaling purposes. An `AbstractScheme` is always the base case, and signals application to the entirety of `A`, whereas an `ExtendScheme` signals that `A` should first be partitioned according to the inner index defined by the entity-being wrapped (`e.s.g` if `ExtendScheme(Scheme)`, or `e.s.h` if `ExtendScheme(ExtendScheme(...))`), and the `Scheme`/`ExtendScheme` applied to each partition. Each partition consists of a contiguous range, across which `g` (or `h`) has the same value; hence, this value serves as the index of the partition.

See also: [`tiles`](@ref)

# Examples

```jldoctest
julia> A = [10 1 1
            20 1 1
            30 1 1
            10 2 1
            20 2 1
            30 2 2
            10 3 2
            20 3 2
            10 4 2
            20 4 2];

julia> B = eachrow(A);

julia> s = @scheme sum x -> x[begin+1] last;


julia> x = tile(s, B)
4-element Tile{Vector{Tile{Vector{Int64}, Int64, Tuple{Int64}, Int64, 1}}, Tile{Vector{Int64}, Int64, Tuple{Int64}, Int64, 1}, Tuple{Int64}, Int64, 1}:
 [12, 22, 32]
 [13, 23, 34]
 [15, 25]
 [16, 26]
```
