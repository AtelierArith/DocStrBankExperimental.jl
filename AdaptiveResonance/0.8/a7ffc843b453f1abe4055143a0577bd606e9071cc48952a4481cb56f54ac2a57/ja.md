```julia
FuzzyART(
    opts::AdaptiveResonance.opts_FuzzyART
) -> AdaptiveResonance.FuzzyART

```

# 概要

指定されたオプションを持つFuzzy ART学習器を実装します。

# 引数

  * `opts::opts_FuzzyART`: 指定されたオプションを持つFuzzyARTオプション構造体（[`AdaptiveResonance.opts_FuzzyART`](@ref）を参照）。

# 例

```julia-repl
julia> FuzzyART(opts)
FuzzyART
    opts: opts_FuzzyART
    ...
```

# メソッドリスト / 定義場所

```julia
FuzzyART(opts)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl:214`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl)で定義されています。
