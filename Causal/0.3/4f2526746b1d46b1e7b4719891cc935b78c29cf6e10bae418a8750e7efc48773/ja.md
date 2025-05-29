```julia
struct Memory{D, IN, TB, DB, IP, OP, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractMemory
```

`Memory`を`input`バスで構築します。`Memory`は`input`の値を`numdelay`の量だけ遅延させます。`initial`は`Memory`からの過渡的な出力を決定します。つまり、`Memory`の内部バッファが満杯になるまで、`initial`からの値が返されます。

# フィールド

  * `delay::Any`: 秒単位の遅延
  * `initial::Any`: メモリの初期値
  * `numtaps::Int64`: メモリのタップ数。タップ数はメモリの内部（timebuf, databuf）バッファの長さです
  * `timebuf::Any`: 時間の瞬間を記録するためのメモリの時間バッファ
  * `databuf::Any`: 入力データ値を記録するためのメモリのデータバッファ
  * `input::Any`: 入力ポート
  * `output::Any`: 出力ポート
  * `readout::Any`: 読み出し関数
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`

# 例

```jldoctest
julia> Memory(delay=0.1)
Memory(delay:0.1, numtaps:5, input:Inport(numpins:1, eltype:Inpin{Float64}), output:Outport(numpins:1, eltype:Outpin{Float64}))

julia> Memory(delay=0.1, numtaps=5)
Memory(delay:0.1, numtaps:5, input:Inport(numpins:1, eltype:Inpin{Float64}), output:Outport(numpins:1, eltype:Outpin{Float64}))
```
