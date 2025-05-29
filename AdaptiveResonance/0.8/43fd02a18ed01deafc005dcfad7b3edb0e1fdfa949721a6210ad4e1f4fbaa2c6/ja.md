```julia
DVFA(; kwargs...) -> AdaptiveResonance.DVFA

```

# 概要

オプションのキーワード引数を持つDVFA学習者を実装します。

# 引数

  * `kwargs`: DVFAオプション構造体に渡すキーワード引数（[`AdaptiveResonance.opts_DVFA`](@ref)を参照してください。）

# 例

デフォルトでは:

```julia-repl
julia> DVFA()
DVFA
    opts: opts_DVFA
    ...
```

またはキーワード引数を使用して:

```julia-repl
julia> DVFA(rho=0.7)
DVFA
    opts: opts_DVFA
    ...
```

# メソッドリスト / 定義場所

```julia
DVFA(; kwargs...)
```

[`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/DVFA.jl:189`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/DVFA.jl)で定義されています。
