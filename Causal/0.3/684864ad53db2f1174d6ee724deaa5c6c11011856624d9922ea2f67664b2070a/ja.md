```julia
struct Terminator{IP, OP, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractStaticSystem
```

`input`バスを持つ`Terminator`を構築します。出力関数`g`は`nothing`に等しいです。`Terminator`は、`input`から流入するデータを受け取るためだけに使用されます。

# フィールド

  * `input::Any`: 入力ポート
  * `output::Any`: 出力。何もない必要があります
  * `readout::Any`: 読み出し関数。何もない必要があります
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
