```julia
opts_DAM(; kwargs...) -> AdaptiveResonance.opts_SFAM

```

# 概要

デフォルトのARTMAPモジュールのオプションを実装します。

デフォルトARTMAPはSFAMの変種であり、[`AdaptiveResonance.opts_SFAM`](@ref)オプションを使用します。このコンストラクタは、提供されたキーワード引数オプションに加えて、アクティベーションを`:choice_by_difference`に設定します。

これらのオプションは、カスタムオプションのキーワード引数を受け取る[`Parameters.jl`](https://github.com/mauro3/Parameters.jl)構造体です。各フィールドには、以下に示すデフォルト値があります。

# メソッドリスト / 定義場所

```julia
opts_DAM(; kwargs...)
```

[`packages/AdaptiveResonance/wgSPV/src/ARTMAP/variants.jl:52`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/variants.jl)で定義されています。
