```julia
DDVFA(
    opts::AdaptiveResonance.opts_DDVFA
) -> AdaptiveResonance.DDVFA

```

# 概要

指定されたオプションを持つDDVFA学習器を実装します。

# 引数

  * `opts::opts_DDVFA`: DDVFAオプション（[`AdaptiveResonance.opts_DDVFA`](@ref)を参照）。

# 例

```julia-repl
julia> my_opts = opts_DDVFA()
julia> DDVFA(my_opts)
DDVFA
    opts: opts_DDVFA
    subopts: opts_FuzzyART
    ...
```

# メソッドリスト / 定義場所

```julia
DDVFA(opts)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/distributed/modules/DDVFA.jl:227`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/distributed/modules/DDVFA.jl)で定義されています。
