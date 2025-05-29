```
PairDistanceEncoding <: Encoding
PairDistanceEncoding(min_dist, max_dist; n = 2, metric = Chebyshev(), precise = false)
```

An encoding that [`encode`](@ref)s point pairs of the form  `Tuple{<:AbstractVector, <:AbstractVector}` by first computing their distance  using the given `metric`, then dividing the interval [`min_dist, max_dist]` into  `n` equal-size bins, and mapping the computed distance onto one of those bins. Bins are enumerated as `1:n`. When [`decode`](@ref)-ing the bin integer, the left edge of the bin is returned.

`precise` has the same meaning as in [`RectangularBinEncoding`](@ref).

## Example

Let's create an example where the minimum and maximum allowed distance is known.

```julia
using ComplexityMeasures, Distances, StaticArrays
m = Chebyshev()
y = [SVector(1.0), SVector(0.5), SVector(0.25), SVector(0.64)]
pair1, pair2, pair3 = (y[1], y[2]), (y[2], y[3]), (y[3], y[4])
dmax = m(pair1...) # dist = 0.50
dmin = m(pair2...) # dist = 0.25
dmid = m(pair3...) # dist = 0.39

# This should give five bins with left adges at [0.25], [0.30], [0.35], [0.40] and [0.45]
encoding = PairDistanceEncoding(dmin, dmax; n = 5, metric = m)
c1 = encode(encoding, pair1) # 5
c2 = encode(encoding, pair2) # 1
c3 = encode(encoding, pair3) # 3

decode(encoding, c3) ≈ [0.35] # true
```
