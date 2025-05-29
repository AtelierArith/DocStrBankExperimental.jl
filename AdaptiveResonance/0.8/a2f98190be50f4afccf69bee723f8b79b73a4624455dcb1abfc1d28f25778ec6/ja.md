```julia
FuzzyART(
    opts::AdaptiveResonance.opts_FuzzyART,
    sample::AbstractVector{T} where T<:Real;
    preprocessed
) -> AdaptiveResonance.FuzzyART

```

# 概要

FuzzyARTを単一のサンプルで一度に作成および初期化します。

主にDDVFA内での初期化の方法として使用されます。

# 引数

  * `opts::opts_FuzzyART`: FuzzyARTオプションを含みます。
  * `sample::RealVector`: FuzzyARTの設定の基礎として使用するサンプル。
  * `preprocessed::Bool=false`: サンプルがすでに補完符号化され、正規化されているかどうかのフラグ。

# メソッドリスト / 定義場所

```julia
FuzzyART(opts, sample; preprocessed)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl:247`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl)で定義されています。
