```julia
DAM(
    opts::AdaptiveResonance.opts_SFAM
) -> AdaptiveResonance.SFAM

```

# 概要

指定されたオプションを持つデフォルトのARTMAPモジュールを実装します。

デフォルトのARTMAPはSFAMの変種であり、[`AdaptiveResonance.opts_SFAM`](@ref)オプションを使用します。このコンストラクタは、提供されたキーワード引数オプションに加えて、アクティベーションを`:choice_by_difference`に設定します。

# 引数

  * `opts::opts_SFAM`: 簡略化されたFuzzyARTMAPオプション（[`AdaptiveResonance.opts_SFAM`](@ref）を参照）。

# メソッドリスト / 定義場所

```julia
DAM(opts)
```

[`packages/AdaptiveResonance/wgSPV/src/ARTMAP/variants.jl:41`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/variants.jl)で定義されています。
