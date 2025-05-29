```julia
struct FunctionGenerator{RO, OP<:Causal.Outport, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractSource
```

汎用関数ジェネレーターを構築します。`readout` 関数と `output` ポートを持ちます。

# フィールド

  * `readout::Any`: 読み出し関数
  * `output::Causal.Outport`: 出力ポート
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`

# 例

```jldoctest
julia> gen = FunctionGenerator(readout = t -> [t, 2t], output = Outport(2));

julia> gen.readout(1.)
2-element Array{Float64,1}:
 1.0
 2.0
```
