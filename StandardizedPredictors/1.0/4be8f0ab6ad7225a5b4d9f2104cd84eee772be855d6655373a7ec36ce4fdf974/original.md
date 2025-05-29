```
struct ZScoredTerm{T,C,S} <: AbstractTerm
```

A lazily z-scored term. A wrapper around an `T<:AbstractTerm` which will produce scaled values with `modelcols` by subtracting `center` from each element and then dividing by `scale`.

## Fields

  * `term::T`: The wrapped term.
  * `center::C`: The center value which is subtracted from the resulting `modelcols`.
  * `scale::S`: The scale value which the resulting `modelcols` are divided by.

## Examples

Directly construct with given scale:

```
julia> d = (x=collect(1:10), );

julia> t = concrete_term(term(:x), d)
x(continuous)

julia> ts = ZScoredTerm(t, 3, 5)
x(centered: 3 scaled: 5)

julia> hcat(modelcols(t + ts, d)...)
10×2 Matrix{Float64}:
  1.0  -0.4
  2.0  -0.2
  3.0   0.0
  4.0   0.2
  5.0   0.4
  6.0   0.6
  7.0   0.8
  8.0   1.0
  9.0   1.2
 10.0   1.4
```

Construct with lazy scaling via [`ZScore`](@ref)

```
julia> ts = concrete_term(term(:x), d, ZScore())
x(centered: 5.5 scaled: 3.03)

julia> hcat(modelcols(t + ts, d)...)
10×2 Matrix{Float64}:
  1.0  -1.4863
  2.0  -1.15601
  3.0  -0.825723
  4.0  -0.495434
  5.0  -0.165145
  6.0   0.165145
  7.0   0.495434
  8.0   0.825723
  9.0   1.15601
 10.0   1.4863
```

Or similarly via schema hints:

```
julia> sch = schema(d, Dict(:x => ZScore()))
StatsModels.Schema with 1 entry:
  x => x(centered: 5.5 scaled: 3.03)
```
