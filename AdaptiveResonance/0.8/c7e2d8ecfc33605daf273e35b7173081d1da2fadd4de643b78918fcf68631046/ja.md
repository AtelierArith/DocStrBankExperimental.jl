```julia
FAM(; kwargs...) -> AdaptiveResonance.FAM

```

# 概要

オプションのキーワード引数を持つFuzzy ARTMAP学習器を実装します。

# 例

デフォルトでは:

```julia-repl
julia> FAM()
FAM
    opts: opts_FAM
    ...
```

またはキーワード引数を使って:

```julia-repl
julia> FAM(rho=0.7)
FAM
    opts: opts_FAM
    ...
```

# メソッドリスト / 定義場所

```julia
FAM(; kwargs...)
```

[`packages/AdaptiveResonance/wgSPV/src/ARTMAP/FAM.jl:129`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/FAM.jl)で定義されています。
