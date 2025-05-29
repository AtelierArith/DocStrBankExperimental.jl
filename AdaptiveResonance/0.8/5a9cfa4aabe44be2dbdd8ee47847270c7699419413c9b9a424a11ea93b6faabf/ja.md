```julia
GammaNormalizedFuzzyART(
    opts::AdaptiveResonance.opts_FuzzyART
)

```

# 概要

指定されたオプションを使用して、Gamma正規化FuzzyARTモジュールを実装します。

GammaNormalizedFuzzyARTは、[`FuzzyART`](@ref)のバリアントであり、[`AdaptiveResonance.opts_FuzzyART`](@ref)オプションを使用します。このコンストラクタは`gamma_normalization=true`を渡し、内部的に`match=:gamma_match`および`activation=:gamma_activation`を使用し、提供されたキーワード引数オプションに加えます。

# 引数

  * `opts::opts_FuzzyART`: Fuzzy ARTオプション（[`AdaptiveResonance.opts_FuzzyART`](@ref）を参照）。

# メソッドリスト / 定義場所

```julia
GammaNormalizedFuzzyART(opts)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/variants.jl:39`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/variants.jl)で定義されています。
