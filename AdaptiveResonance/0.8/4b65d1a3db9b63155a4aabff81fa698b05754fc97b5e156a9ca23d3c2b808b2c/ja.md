```julia
opts_GammaNormalizedFuzzyART(; kwargs...)

```

# 概要

Gamma-Normalized FuzzyARTモジュールのオプションを実装します。

GammaNormalizedFuzzyARTは、[`FuzzyART`](@ref)のバリアントであり、[`AdaptiveResonance.opts_FuzzyART`](@ref)オプションを使用します。このコンストラクタは`gamma_normalization=true`を渡し、内部的に`match=:gamma_match`と`activation=:gamma_activation`を使用し、提供されたキーワード引数オプションに加えます。

これらのオプションは、カスタムオプションのキーワード引数を受け取る[`Parameters.jl`](https://github.com/mauro3/Parameters.jl)構造体です。各フィールドには、以下に示すデフォルト値があります。

# メソッドリスト / 定義場所

```julia
opts_GammaNormalizedFuzzyART(; kwargs...)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/variants.jl:50`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/variants.jl)で定義されています。
