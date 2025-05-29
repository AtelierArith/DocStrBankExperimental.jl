```julia
mutable struct Scope{A, PA, PK, PLT, var"356", var"357", var"358", Symbol, var"359", var"366", Int, var"367", var"368", var"369", var"370"} <: Causal.AbstractSink
```

入力バス `input` を持つ `Scope` を構築します。`buflen` は `Scope` の内部バッファの長さです。`plugin` は追加のデータ処理ツールです。`args`,`kwargs` は `plots(args...; kwargs...)` に渡されます。詳細については (https://github.com/JuliaPlots/Plots.jl) を参照してください。

!!! warning 初期化時に、`Scope` の `plot` は閉じられています。 [`open(sink::Scope)`](@ref) と [`close(sink::Scope)`](@ref) を参照してください。

# フィールド

  * `action::Any`: データを更新するためのコンポーネントのアクション
  * `pltargs::Any`: プロット引数
  * `pltkwargs::Any`: プロットキーワード引数
  * `plt::Any`: コンポーネントのプロットオブジェクト
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
  * `input::Any`
  * `buflen::Any`
  * `plugin::Any`
  * `timebuf::Any`
  * `databuf::Any`
  * `sinkcallback::Any`
