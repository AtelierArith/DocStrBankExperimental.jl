```
LazyModel{Name, T} <: AbstractMillModel
```

A model node for processing [`LazyNode`](@ref)s. It applies a (sub)model `m` stored in it to data of the [`LazyNode`](@ref) after calling [`Mill.unpack2mill`](@ref).

# Examples

```julia-repl
julia> function Mill.unpack2mill(ds::LazyNode{:Sentence})
    s = split.(ds.data, " ")
    x = NGramMatrix(reduce(vcat, s))
    BagNode(x, Mill.length2bags(length.(s)))
end
```

```jldoctest unpack2mill
julia> Random.seed!(0);

julia> n = LazyNode{:Sentence}(["foo", "bar", "baz"])
LazyNode{:Sentence, Vector{String}, Nothing}:
 "foo"
 "bar"
 "baz"

julia> m = LazyModel{:Sentence}(BagModel(Dense(2053, 3), SegmentedMean(3), identity))
LazyModel{Sentence}
  ╰── BagModel ↦ SegmentedMean(3) ↦ identity  1 arrays, 3 params (all zero), 52 bytes
        ╰── ArrayModel(Dense(2053 => 3))  2 arrays, 6_162 params, 24.156 KiB
```

```jldoctest unpack2mill; filter=r"\s*-?[0-9]+\.[0-9]+[\.]*\s*"
julia> m(n)
3×3 Matrix{Float32}:
 -0.06... -0.03... -0.04...
  0.02...  0.00... -0.07...
 -0.00...  0.06... -0.07...
```

See also: [`AbstractMillModel`](@ref), [`LazyNode`](@ref), [`Mill.unpack2mill`](@ref).
