```julia
GammaNormalizedFuzzyART(
;
    kwargs...
) -> AdaptiveResonance.FuzzyART

```

# 概要

ガンマ正規化FuzzyARTモジュールを、ガンマ正規化オプションを使用してFuzzyARTのバリアントとして構築します。

GammaNormalizedFuzzyARTは、[`FuzzyART`](@ref)のバリアントであり、[`AdaptiveResonance.opts_FuzzyART`](@ref)オプションを使用しています。このコンストラクタは`gamma_normalization=true`を渡し、内部的に`match=:gamma_match`と`activation=:gamma_activation`を使用し、さらに提供されたキーワード引数オプションを使用します。

# 引数

  * `kwargs`: FuzzyARTオプションのキーワード引数（[`AdaptiveResonance.opts_FuzzyART`](@ref）を参照）

# メソッドリスト / 定義場所

```julia
GammaNormalizedFuzzyART(; kwargs...)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/variants.jl:26`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/variants.jl)で定義されています。
