```julia
struct StaticSystem{RO, IP, OP, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractStaticSystem
```

汎用の静的システムを`readout`関数、`input`ポート、および`output`ポートで構築します。

# フィールド

  * `readout::Any`: 読み出し関数
  * `input::Any`: 入力ポート
  * `output::Any`: 出力。`Outport`または`Nothing`である可能性があります
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`

# 例

```jldoctest
julia> ss = StaticSystem(readout = (t,u) -> u[1] + u[2], input=Inport(2), output=Outport(1));

julia> ss.readout(0., ones(2))
2.0
```
