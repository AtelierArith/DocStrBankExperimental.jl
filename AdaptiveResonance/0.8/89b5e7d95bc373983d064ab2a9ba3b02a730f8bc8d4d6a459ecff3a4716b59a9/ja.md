```julia
FuzzyART(; kwargs...) -> AdaptiveResonance.FuzzyART

```

# 概要

オプションのキーワード引数を持つFuzzy ART学習器を実装します。

# 引数

  * `kwargs`: FuzzyARTオプションのキーワード引数（[`AdaptiveResonance.opts_FuzzyART`](@ref)を参照）。

# 例

デフォルトでは:

```julia-repl
julia> FuzzyART()
FuzzyART
    opts: opts_FuzzyART
    ...
```

またはキーワード引数を使用して:

```julia-repl
julia> FuzzyART(rho=0.7)
FuzzyART
    opts: opts_FuzzyART
    ...
```

# メソッドリスト / 定義場所

```julia
FuzzyART(; kwargs...)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl:192`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl)で定義されています。
