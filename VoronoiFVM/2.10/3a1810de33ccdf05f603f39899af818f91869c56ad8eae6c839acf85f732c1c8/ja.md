```julia
fbernoulli(x)

```

ベルヌーイ関数 $B(x)=\frac{x}{e^x-1}$ は指数的にフィットしたアップウィンドに使用されます。

名前 `fbernoulli` は、JuliaStats/Distributions.jl の `Bernoulli` との混同を避けるために選ばれました。

結果を含む実数を返します。

`x/expm1(x)` はすべての `x!=0` に対して十分に正確であるように見えますが、`ForwardDiff.jl` を介して計算されたその導関数はそうではないため、区間 `(-bernoulli_small_threshold, bernoulli_small_threshold)` では多項式近似を使用します。

また、[＃117](https://github.com/WIAS-PDELib/VoronoiFVM.jl/issues/117) の議論も参照してください。
