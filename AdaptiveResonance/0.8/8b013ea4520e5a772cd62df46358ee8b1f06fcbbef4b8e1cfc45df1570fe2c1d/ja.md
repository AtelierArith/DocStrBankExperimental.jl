```julia
SFAM(
    opts::AdaptiveResonance.opts_SFAM
) -> AdaptiveResonance.SFAM

```

# 概要

指定されたオプションを持つシンプルファジーARTMAP学習器を実装します。

# 引数

  * `opts::opts_SFAM`: シンプルファジーARTMAPオプション（[`AdaptiveResonance.opts_SFAM`](@ref)を参照）。

# 例

```julia-repl
julia> opts = opts_SFAM()
julia> SFAM(opts)
SFAM
    opts: opts_SFAM
    ...
```

# メソッドリスト / 定義場所

```julia
SFAM(opts)
```

[`packages/AdaptiveResonance/wgSPV/src/ARTMAP/SFAM.jl:186`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/SFAM.jl)で定義されています。
