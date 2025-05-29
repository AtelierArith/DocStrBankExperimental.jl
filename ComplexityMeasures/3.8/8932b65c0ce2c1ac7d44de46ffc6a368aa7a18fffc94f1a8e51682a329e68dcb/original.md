```
GaussianCDFEncoding <: Encoding
GaussianCDFEncoding{m}(; μ, σ, c::Int = 3)
```

An encoding scheme that [`encode`](@ref)s a scalar or vector `χ` into one of the integers `sᵢ ∈ [1, 2, …, c]` based on the normal cumulative distribution function (NCDF), and [`decode`](@ref)s the `sᵢ` into subintervals of `[0, 1]` (with some loss of information).

## Initializing a `GaussianCDFEncoding`

The size of the input to be encoded must be known beforehand. One must therefore set `m = length(χ)`, where `χ` is the input (`m = 1` for scalars, `m ≥ 2` for vectors). To do so, one must explicitly give `m` as a type parameter: e.g. `encoding = GaussianCDFEncoding{3}(; μ = 0.0, σ = 0.1)` to encode 3-element vectors, or `encoding = GaussianCDFEncoding{1}(; μ = 0.0, σ = 0.1)` to encode scalars.

## Description

### Encoding/decoding scalars

`GaussianCDFEncoding` first maps an input scalar $χ$ to a new real number $y_ \in [0, 1]$ by using the normal cumulative distribution function (CDF) with the given mean `μ` and standard deviation `σ`, according to the map

$$
x \to y : y = \dfrac{1}{ \sigma
    \sqrt{2 \pi}} \int_{-\infty}^{x} e^{(-(x - \mu)^2)/(2 \sigma^2)} dx.
$$

Next, the interval `[0, 1]` is equidistantly binned and enumerated $1, 2, \ldots, c$,  and $y$ is linearly mapped to one of these integers using the linear map  $y \to z : z = \text{floor}(y(c-1)) + 1$.

Because of the floor operation, some information is lost, so when used with [`decode`](@ref), each decoded `sᵢ` is mapped to a *subinterval* of `[0, 1]`. This subinterval is returned as a length-`1` `Vector{SVector}`.

Notice that the decoding step does not yield an element of any outcome space of the estimators that use `GaussianCDFEncoding` internally, such as [`Dispersion`](@ref). That is because these estimators additionally delay embed the encoded data.

### Encoding/decoding vectors

If `GaussianCDFEncoding` is used with a vector `χ`, then each element of `χ` is encoded separately, resulting in a `length(χ)` sequence of integers which may be treated as a `CartesianIndex`. The encoded symbol `s ∈ [1, 2, …, c]` is then just the linear index corresponding to this cartesian index (similar to how [`CombinationEncoding`](@ref) works).

When [`decode`](@ref)d, the integer symbol `s` is converted back into its `CartesianIndex` representation,  which is just a sequence of integers that refer to subdivisions of the `[0, 1]` interval. The relevant subintervals are then returned as a length-`χ` `Vector{SVector}`.

## Examples

```jldoctest
julia> using ComplexityMeasures, Statistics

julia> x = [0.1, 0.4, 0.7, -2.1, 8.0];

julia> μ, σ = mean(x), std(x); encoding = GaussianCDFEncoding(; μ, σ, c = 5)

julia> es = encode.(Ref(encoding), x)
5-element Vector{Int64}:
 2
 2
 3
 1
 5

julia> decode(encoding, 3)
2-element SVector{2, Float64} with indices SOneTo(2):
 0.4
 0.6
```
