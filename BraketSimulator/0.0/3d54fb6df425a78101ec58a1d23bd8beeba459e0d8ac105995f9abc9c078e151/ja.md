```
simulate(simulator::AbstractSimulator, circuit_ir::Union{OpenQasmProgram, Program}, shots::Int; kwargs...) -> GateModelTaskResult
```

渡された `simulator` を使用して状態ベクトルまたは密度行列の進化をシミュレートします。適用する指示（ゲートとノイズチャネル）および行う測定は `circuit_ir` にエンコードされています。サポートされているIRフォーマットは `OpenQASMProgram` (OpenQASM3) と `Program` (JAQCD) です。`shots > 0` の場合、個々のショット測定、最終的に計算された結果、回路IR、およびタスクに関するメタデータを含む `GateModelTaskResult` を返します。
