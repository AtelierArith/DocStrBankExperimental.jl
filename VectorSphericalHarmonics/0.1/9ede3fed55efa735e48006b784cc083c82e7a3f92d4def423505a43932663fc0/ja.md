```
genspharm(modes::Union{SphericalHarmonicModes.LM, SphericalHarmonicModes.ML}, θ, ϕ, [S = maximum(SphericalHarmonicModes.l_range(modes))])
```

Phinney-Burridge（[`PB`](@ref)）ベクトル球面調和関数の対角要素を、`modes`内のすべてのモード`(j,m)`に対して[`HelicityCovariant`](@ref)基底で評価します。

事前に割り当てられたスカラー球面調和関数の配列`S`を最後の引数として渡すことができます。これは[`VectorSphericalHarmonics.cache`](@ref)を使用して生成できます。
