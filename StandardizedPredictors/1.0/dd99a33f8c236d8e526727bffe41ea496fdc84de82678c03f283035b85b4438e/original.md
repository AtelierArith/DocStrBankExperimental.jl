```
struct ScaledTerm{T,S} <: AbstractTerm
```

A lazily scaled term.  A wrapper around an `T<:AbstractTerm` which will produce scaled values with `modelcols` by dividing each element by `scale`.

## Fields

  * `term::T`: The wrapped term.
  * `scale::S`: The scale value which the resulting `modelcols` are divided by.

## Examples

Directly construct with given scale:

```
julia> d = (x=collect(1:10), );

julia> t = concrete_term(term(:x), d)
x(continuous)

julia> ts = ScaledTerm(t, 5)
x(scaled: 5)

julia> hcat(modelcols(t + ts, d)...)
10×2 Matrix{Float64}:
  1.0  0.2
  2.0  0.4
  3.0  0.6
  4.0  0.8
  5.0  1.0
  6.0  1.2
  7.0  1.4
  8.0  1.6
  9.0  1.8
 10.0  2.0
```

Construct with lazy scaling via [`Scale`](@ref)

```
julia> ts = concrete_term(term(:x), d, Scale())
x(scaled: 3.03)

julia> hcat(modelcols(t + ts, d)...)
10×2 Matrix{Float64}:
  1.0  0.330289
  2.0  0.660578
  3.0  0.990867
  4.0  1.32116
  5.0  1.65145
  6.0  1.98173
  7.0  2.31202
  8.0  2.64231
  9.0  2.9726
 10.0  3.30289
```

Or similarly via schema hints:

```
julia> sch = schema(d, Dict(:x => Scale()))
StatsModels.Schema with 1 entry:
  x => scale(x, 3.03)
```
