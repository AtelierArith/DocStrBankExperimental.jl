```julia
DAM(; kwargs...) -> AdaptiveResonance.SFAM

```

# 概要

デフォルトのARTMAPモジュールをSFAMモジュールを使用して構築します。これは、デフォルトのARTMAPの選択による差異活性化関数を使用します。

デフォルトのARTMAPはSFAMの変種であり、[`AdaptiveResonance.opts_SFAM`](@ref)オプションを使用します。このコンストラクタは、提供されたキーワード引数オプションに加えて、活性化を`:choice_by_difference`に設定します。

# 引数

  * `kwargs`: 簡略化されたFuzzyARTMAPオプションのキーワード引数（[`AdaptiveResonance.opts_SFAM`](@ref）を参照）

# 参考文献:

1. G. P. Amis and G. A. Carpenter, 'Default ARTMAP 2,' IEEE Int. Conf. Neural Networks - Conf. Proc., vol. 2, no. September 2007, pp. 777-782, Mar. 2007, doi: 10.1109/IJCNN.2007.4371056.

# メソッドリスト / 定義場所

```julia
DAM(; kwargs...)
```

[`packages/AdaptiveResonance/wgSPV/src/ARTMAP/variants.jl:29`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/variants.jl)で定義されています。
