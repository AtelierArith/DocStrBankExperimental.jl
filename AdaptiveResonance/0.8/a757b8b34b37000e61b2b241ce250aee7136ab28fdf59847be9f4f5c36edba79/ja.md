```julia
SFAM(; kwargs...) -> AdaptiveResonance.SFAM

```

# 概要

オプションのキーワード引数を持つシンプルファジーARTMAP学習器を実装します。

# 引数

  * `kwargs`: シンプルファジーARTMAPオプション構造体に渡すキーワード引数（[`AdaptiveResonance.opts_SFAM`](@ref)を参照してください。）

# 例

デフォルトでは:

```julia-repl
julia> SFAM()
SFAM
    opts: opts_SFAM
    ...
```

またはキーワード引数を使用して:

```julia-repl
julia> SFAM(rho=0.6)
SFAM
    opts: opts_SFAM
    ...
```

# メソッドリスト / 定義場所

```julia
SFAM(; kwargs...)
```

[`packages/AdaptiveResonance/wgSPV/src/ARTMAP/SFAM.jl:166`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/SFAM.jl)で定義されています。
