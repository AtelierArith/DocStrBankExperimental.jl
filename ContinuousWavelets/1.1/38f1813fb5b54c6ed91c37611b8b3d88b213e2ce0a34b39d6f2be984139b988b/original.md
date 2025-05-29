```
waveletCoherence(X, Y, c)
```

Compute the wavelet coherence between `X` and `Y`. This is given by the power of the cross spectrum, normalized by smoothed powers of both `X` and `Y`. Explicitly, that is $\frac{|S(C^*(X)C(Y))|^2}{S(|C(X)|^2)S(|C(Y)|^2)}$.

# Examples

```jldoctest ex
julia> using ContinuousWavelets, Random

julia> rng = MersenneTwister(23425); Y = randn(rng, 2053, 4);

julia> X = Y .+ 3;

julia> c = wavelet(morl,β=2);

julia> wCo = waveletCoherence(X, Y, c);


julia> wCo[:,:,1,1]
2053×29 Matrix{Float64}:
 0.688432  1.0  1.0  1.0  1.0  …  1.0  1.0  1.0  1.0  1.0
 0.687333  1.0  1.0  1.0  1.0     1.0  1.0  1.0  1.0  1.0
 ⋮                             ⋱       ⋮
 0.952408  1.0  1.0  1.0  1.0     1.0  1.0  1.0  1.0  1.0
 0.952626  1.0  1.0  1.0  1.0     1.0  1.0  1.0  1.0  1.0

julia> wCo[:,:,1,2]
2053×29 Matrix{Float64}:
 0.995092  0.984109  0.952974  …  0.128329  0.0335945
 0.995082  0.984082  0.952852     0.128308  0.0336075
 ⋮                             ⋱
 0.652498  0.994972  0.992932     0.19849   0.0902301
 0.653111  0.994978  0.992951     0.198585  0.0902469

```
