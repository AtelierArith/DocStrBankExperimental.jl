`Path(isym[,osym], iolabel::Pair, w=one(TropicalWeight{Float32}))`

Construct a path with input and output symbol table `isym` and (optional) `osym` (see [`WFST`](@ref)).

`iolabel` is a `Pair` of vectors.

```julia
julia> isym = ["a","b","c","d"];

julia> osym = ["α","β","γ","δ"];

julia> W = ProbabilityWeight{Float32};

julia> p = Path(isym,osym,["a","b","c"] => ["α","β","γ"], one(W))
["a", "b", "c"] → ["α", "β", "γ"], w:1.0f0

```

The weight of a path of a WFST results from the multiplication ($\otimes$) of the weights of the different arcs that are transversed. See e.g. [`get_paths`](@ref) to extract paths from a WFST.

```julia
julia> p * Path(isym,osym,["d"] => ["δ"], W(0.5))
["a", "b", "c", "d"] → ["α", "β", "γ", "δ"], w:0.5f0

```
