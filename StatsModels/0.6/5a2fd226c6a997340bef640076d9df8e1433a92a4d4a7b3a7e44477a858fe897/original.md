```
schema([terms::AbstractVector{<:AbstractTerm}, ]data, hints::Dict{Symbol})
schema(term::AbstractTerm, data, hints::Dict{Symbol})
```

Compute all the invariants necessary to fit a model with `terms`.  A schema is a dict that maps `Term`s to their concrete instantiations (either `CategoricalTerm`s or `ContinuousTerm`s.  "Hints" may optionally be supplied in the form of a `Dict` mapping term names (as `Symbol`s) to term or contrast types.  If a hint is not provided for a variable, the appropriate term type will be guessed based on the data type from the data column: any numeric data is assumed to be continuous, and any non-numeric data is assumed to be categorical.

Returns a [`StatsModels.Schema`](@ref), which is a wrapper around a `Dict` mapping `Term`s to their concrete instantiations (`ContinuousTerm` or `CategoricalTerm`).

# Example

```jldoctest 1
julia> using StableRNGs; rng = StableRNG(1);

julia> d = (x=sample(rng, [:a, :b, :c], 10), y=rand(rng, 10));

julia> ts = [Term(:x), Term(:y)];

julia> schema(ts, d)
StatsModels.Schema with 2 entries:
  x => x
  y => y

julia> schema(ts, d, Dict(:x => HelmertCoding()))
StatsModels.Schema with 2 entries:
  x => x
  y => y

julia> schema(term(:y), d, Dict(:y => CategoricalTerm))
StatsModels.Schema with 1 entry:
  y => y
```

Note that concrete `ContinuousTerm` and `CategoricalTerm` and un-typed `Term`s print the same in a container, but when printed alone are different:

```jldoctest 1
julia> sch = schema(ts, d)
StatsModels.Schema with 2 entries:
  x => x
  y => y

julia> term(:x)
x(unknown)

julia> sch[term(:x)]
x(DummyCoding:3→2)

julia> sch[term(:y)]
y(continuous)
```
