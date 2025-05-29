```julia
mutable struct Printer{A, var"356", var"357", var"358", Symbol, var"359", var"366", Int, var"367", var"368", var"369", var"370"} <: Causal.AbstractSink
```

入力バス `input` を持つ `Printer` を構築します。`buflen` は内部 `buflen` の長さです。`plugin` はデータ処理ツールです。

# フィールド

  * `action::Any`: データを印刷するシンクのアクション
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
