```
GP{Tm<:MeanFunction, Tk<:Kernel}
```

既知の`mean`と`kernel`を持つガウス過程（GP）。例えば、[1]を参照してください。

# ゼロ平均

引数が1つだけ提供された場合、平均はどこでもゼロであると仮定します：

```jldoctest
julia> f = GP(Matern32Kernel());

julia> x = randn(5);

julia> mean(f(x)) == zeros(5)
true

julia> cov(f(x)) == kernelmatrix(Matern32Kernel(), x)
true
```

### 定数平均

最初の引数として`Real`が提供された場合、その値で平均関数が定数であると仮定します。

```jldoctest
julia> f = GP(5.0, Matern32Kernel());

julia> x = randn(5);

julia> mean(f(x)) == 5.0 .* ones(5)
true

julia> cov(f(x)) == kernelmatrix(Matern32Kernel(), x)
true
```

### カスタム平均

平均を計算するために任意の関数を提供します：

```jldoctest
julia> f = GP(x -> sin(x) + cos(x / 2), Matern32Kernel());

julia> x = randn(5);

julia> mean(f(x)) == sin.(x) .+ cos.(x ./ 2)
true

julia> cov(f(x)) == kernelmatrix(Matern32Kernel(), x)
true
```

[1] - C. E. Rasmussen and C. Williams. "Gaussian processes for machine learning".  MIT Press. 2006.
