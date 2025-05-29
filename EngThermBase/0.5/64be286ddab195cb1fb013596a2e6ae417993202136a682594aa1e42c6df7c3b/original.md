`struct unvarSerF{𝕡,𝕩} <: AuxFunc where {𝕡<:PREC,𝕩<:EXAC}`

Precision- and Exactness- parameterized, scalar-valued, dimensionless, `<:AbstractFloat`, univariate, series function type with explicit compact (bounded / interval) domain support.

Depending on the Exactness parameter, *both* function domain and codomain elements are uniformly of type `𝕡 where {𝕡<:PREC}`, for `𝕩 ≡ EX` — the Exact base; or `Measurement{𝕡} where {𝕡<:PREC}`, for `𝕩 ≡ MM` — the Measurement base.

Data members include:

```
- `xmin::Union{𝕡, Measurement{𝕡}} where 𝕡<:PREC`: the domain support interval inferior endpoint;
- `xmax::Union{𝕡, Measurement{𝕡}} where 𝕡<:PREC`: the domain support interval superior endpoint;
- `fvec::Vector{Function}`: the variable collection of function additive terms;
- `mulf::Union{𝕡, Measurement{𝕡}} where 𝕡<:PREC`: the multiplicative factor, for %error;
```

The inner constructors enforce the following standards/restrictions:

```
- No input value `{xmin,xmax}` shall be a NaN;
- `xmin <= xmax`;
- `fvec` must not be empty.
```

Instances of `unvarSerF` are `functors`, meaning they can be used as functions (as expected). The functor implementation enforce the following standard: if `𝑓::unvarSerF{𝕡,𝕩} ...`, then:

```
- `𝑓{𝕡,EX}(𝑥)::𝕡 where 𝕡<:PREC`, meaning the return type precision is `EX`;
- `𝑓{𝕡,MM}(𝑥)::Measurement{𝕡} where 𝕡<:PREC`, meaning the return type precision is `MM`;
```

## Hierarchy

`unvarSerF <: AuxFunc <: AUX <: AbstractTherm <: Any`
