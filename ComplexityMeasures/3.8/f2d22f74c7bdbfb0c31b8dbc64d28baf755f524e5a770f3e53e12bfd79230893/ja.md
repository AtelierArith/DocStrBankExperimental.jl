```
PairDistanceEncoding <: Encoding
PairDistanceEncoding(min_dist, max_dist; n = 2, metric = Chebyshev(), precise = false)
```

点のペア `Tuple{<:AbstractVector, <:AbstractVector}` を [`encode`](@ref) するエンコーディングで、まず与えられた `metric` を使用して距離を計算し、その後、区間 [`min_dist, max_dist]` を `n` 個の等サイズのビンに分割し、計算された距離をそれらのビンの1つにマッピングします。ビンは `1:n` として列挙されます。ビンの整数を [`decode`](@ref) すると、ビンの左端が返されます。

`precise` は [`RectangularBinEncoding`](@ref) と同じ意味を持ちます。

## 例

最小および最大の許容距離が知られている例を作成しましょう。

```julia
using ComplexityMeasures, Distances, StaticArrays
m = Chebyshev()
y = [SVector(1.0), SVector(0.5), SVector(0.25), SVector(0.64)]
pair1, pair2, pair3 = (y[1], y[2]), (y[2], y[3]), (y[3], y[4])
dmax = m(pair1...) # dist = 0.50
dmin = m(pair2...) # dist = 0.25
dmid = m(pair3...) # dist = 0.39

# これは [0.25], [0.30], [0.35], [0.40] および [0.45] に左端がある5つのビンを与えるはずです
encoding = PairDistanceEncoding(dmin, dmax; n = 5, metric = m)
c1 = encode(encoding, pair1) # 5
c2 = encode(encoding, pair2) # 1
c3 = encode(encoding, pair3) # 3

decode(encoding, c3) ≈ [0.35] # true
```
