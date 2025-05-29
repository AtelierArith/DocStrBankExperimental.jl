```
crossSpectrum(X, Y, c::CWT)
```

信号 `X` と `Y` のクロススペクトルを計算します。これは $S(\\conj{C(X)})$ と定義されます。`cwt` とは異なり、`crossSpectrum` は形状 (signalLength)×(nSignals) のベクトルのコレクション `X` と `Y` のみで動作し、形状 (signalLength)×(nscales+1)×(nSignalsX)×(nSignalsY) のクロススペクトルのコレクションを出力します。

# 例

```jldoctest
julia> using ContinuousWavelets, Random

julia> rng = MersenneTwister(23425); Y = randn(rng, 2053, 4);

julia> X = Y .+ 3;

julia> c = wavelet(morl, β = 2);

julia> Xspec = crossSpectrum(X, Y, c); size(Xspec)
(2053, 29, 4, 4)

julia> Xspec[:,:,1,1]
2053×29 Matrix{ComplexF64}:
 -4.14517e-5+2.19692e-20im  …  1.19877e-5-7.07215e-15im
 -4.14157e-5+2.23209e-21im     1.19896e-5-7.06562e-15im
            ⋮               ⋱
 0.000119144+4.38332e-21im     1.70054e-5+1.85809e-15im
 0.000119178+1.3884e-20im      1.69993e-5+1.8598e-15im

julia> Xspec[:,:,1,2]
2053×29 Matrix{ComplexF64}:
  5.42995e-5-1.94343e-20im  …    2.649e-6-1.22869e-6im
   5.4303e-5-1.52994e-20im      2.6479e-6-1.23329e-6im
            ⋮               ⋱
 -3.17457e-5-1.12611e-20im     4.71683e-6+3.72814e-6im
 -3.17719e-5+1.44436e-20im     4.71417e-6+3.7279e-6im

```
