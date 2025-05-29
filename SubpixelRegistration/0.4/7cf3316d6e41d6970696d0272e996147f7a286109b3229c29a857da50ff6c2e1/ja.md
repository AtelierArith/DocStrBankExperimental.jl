```
phase_offset(source, target; upsample_factor=1, normalize=false)
```

`source` と `target` の間のシフトを各軸に沿って返します。これは、画像間の相互相関の最大値を測定することによって行われます。このアルゴリズムは、行列乗算DFTを介して相互相関を局所的にアップサンプリングすることにより、`1/upsample_factor` の精度を達成できます。[^1] `normalize` が `true` の場合、フーリエ空間における相互相関の位相はその大きさで割られます。いくつかのアプリケーションでは、位相の正規化が性能を向上させることがありますが、通常は低ノイズ性能が悪化するというトレードオフがあります。

# 例

```jldoctest
julia> image = reshape(1.0:100.0, 10, 10);

julia> shift = (-1.6, 2.8)
(-1.6, 2.8)

julia> target = fourier_shift(image, shift);

julia> phase_offset(image, target)
(shift = (2.0, -3.0), error = 0.013095117382042387, phasediff = 0.0)

julia> phase_offset(image, target; upsample_factor=5)
(shift = (1.6, -2.8), error = -9972.926257260056, phasediff = 0.0)

julia> phase_offset(image, target; upsample_factor=5, normalize=true)
(shift = (1.8, -2.8), error = 0.9999999971143979, phasediff = 0.0)

julia> @. isapprox(ans.shift, -1 * shift, atol=1/5)
(true, true)
```

[^1]: Manuel Guizar-Sicairos, Samuel T. Thurman, and James R. Fienup, ["Efficient subpixel image registration algorithms,"](http://www.opticsinfobase.org/ol/fulltext.cfm?uri=ol-33-2-156&id=148843) Opt. Lett. 33, 156-158 (2008)
