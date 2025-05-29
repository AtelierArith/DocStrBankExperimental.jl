```julia
DDVFA(; kwargs...) -> AdaptiveResonance.DDVFA

```

# 概要

オプションのキーワード引数を持つDDVFA学習器を実装します。

# 引数

  * `kwargs`: DDVFAオプション構造体に渡すキーワード引数（[`AdaptiveResonance.opts_DDVFA`](@ref）を参照してください。）

# 例

デフォルトでは:

```julia-repl
julia> DDVFA()
DDVFA
    opts: opts_DDVFA
    subopts: opts_FuzzyART
    ...
```

またはキーワード引数を使用して:

```julia-repl
julia> DDVFA(rho_lb=0.4, rho_ub = 0.75)
DDVFA
    opts: opts_DDVFA
    subopts: opts_FuzzyART
    ...
```

# メソッドリスト / 定義場所

```julia
DDVFA(; kwargs...)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/distributed/modules/DDVFA.jl:206`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/distributed/modules/DDVFA.jl)で定義されています。
