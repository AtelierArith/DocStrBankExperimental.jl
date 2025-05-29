```julia
DVFA(
    opts::AdaptiveResonance.opts_DVFA
) -> AdaptiveResonance.DVFA

```

# 概要

指定されたオプションを持つDVFA学習器を実装します。

# 引数

  * `opts::opts_DVFA`: DVFAオプション（[`AdaptiveResonance.opts_DVFA`](@ref）を参照）。

# 例

```julia-repl
julia> my_opts = opts_DVFA()
julia> DVFA(my_opts)
DVFA
    opts: opts_DVFA
    ...
```

# メソッドリスト / 定義場所

```julia
DVFA(opts)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/DVFA.jl:209`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/DVFA.jl)で定義されています。
