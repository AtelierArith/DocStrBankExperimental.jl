```
genspharm(j, m, θ, ϕ, [S = VectorSphericalHarmonics.cache(θ, ϕ, j)])
```

Phinney-Burridge ([`PB`](@ref)) ベクトル球面調和関数の対角要素を [`HelicityCovariant`](@ref) 基底でモード `(j,m)` に対して評価します。返される配列 `Y` の要素 `Y[n]` は次のように与えられます。

$$
Y_{jm}^N(\theta,\phi) = \left[\mathbf{P}_{j m}^N(θ, ϕ)\right]^N
$$

これらの成分は、Dahlen & Tromp (1998) によって「一般化された球面調和関数」と呼ばれ、ここでもその用語が使用されています。

スカラー球面調和関数の事前に割り当てられた配列 `S` を最後の引数として渡すことができます。これは [`VectorSphericalHarmonics.cache`](@ref) を使用して生成できます。
