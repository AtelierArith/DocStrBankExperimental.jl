```
simulate(simulator::AbstractSimulator, circuit_irs::Vector{<:Union{Program, OpenQasmProgram}}, shots::Int; max_parallel::Int=min(32, Threads.nthreads()), inputs=Dict{String,Float64}(), kwargs...) -> Vector{GateModelTaskResult}
```

渡された `simulator` を使用して、*バッチ* の状態ベクトルまたは密度行列の進化をシミュレートします。適用する指示（ゲートとノイズチャネル）および測定を行うための指示は `circuit_irs` にエンコードされています。サポートされている IR フォーマットは `OpenQASMProgram` (OpenQASM3) と `Program` (JAQCD) です。

バッチのシミュレーションはスレッドを使用して並行して行われます。キーワード引数 `max_parallel` は、並行してシミュレートする進化の数を指定します - デフォルト値は `32` と `Threads.nthreads()` のうち小さい方です。これは、各進化がスレッド化されているため、実行待ちの小さなタスクが多すぎてスレッドスケジューラを圧倒しないようにするためです。この値は将来的に変更される可能性があります。

`inputs` キーワード引数は `Dict{String}` または `Vector{Dict{String}}` であることができます。最初のケースでは、同じ入力値がすべての `circuit_irs` に適用されます。2 番目の場合、`inputs` の長さは `circuit_irs` の長さと同じでなければならず、`n` 番目の `inputs` が `n` 番目の `circuit_irs` に適用されます。

`Vector{GateModelTaskResult}` を返し、その各要素には個々のショット測定（`shots > 0` の場合）、最終的に計算された結果、対応する回路 IR、およびタスクに関するメタデータが含まれています。
