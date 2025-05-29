```
    z = ePortfolio(mu, aEF::sEF)
    z = ePortfolio(mu, P::Problem; nS=Settings(P), settings, settingsLP)            #one-step, given mu
    z = ePortfolio(P::Problem, L, aCL::Vector{sCL})
    z = ePortfolio(P::Problem, L::T=0.0; nS=Settings(P), settings, settingsLP)      #one-step, given L
```

`ePortfolio(mu::Float64, aEF)` は、効率的フロンティアが知られているときに mu に基づいて効率的ポートフォリオを計算し、ポートフォリオの重み z を返します（mu が範囲外の場合は NaN の Nx1 ベクトル）。

`ePortfolio(mu, P; nS=Settings(P))` は、mu::Float64 を与えられたときに `P` の効率的ポートフォリオを計算し、ポートフォリオの重み z を返します（mu が範囲外の場合は NaN の Nx1 ベクトル）。もし mu が ::Vector{Float64} の場合、z は行列となり、その行 k は mu[k] のためのポートフォリオの重みです。ここでは `init::Function` を設定することはできません。

`ePortfolio(P, L::T, aCL)` は、既知のクリティカルライン `aCL` を持つ `P` の効率的ポートフォリオを、与えられた `L::T`（Float64, BigFloat）に基づいて計算します。

`ePortfolio(P::Problem, L::T=0.0; nS=Settings(P), settings, settingsLP)` は、与えられた `L` に基づいて `P` の効率的ポートフォリオを計算します。

さらに [`EfficientFrontier.ECL`](@ref), [`eFrontier`](@ref), [`Problem`](@ref), [`Settings`](@ref) を参照してください。
