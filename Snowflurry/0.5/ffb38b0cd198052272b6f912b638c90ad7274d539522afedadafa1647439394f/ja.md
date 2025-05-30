```
run_job(qpu::AnyonYukonQPU, circuit::QuantumCircuit, shot_count::Integer)
```

`QPU` サービスに回路を送信して実行します。この関数は、[`transpile_and_run_job`](@ref) のように標準的なトランスパイルを行いません。回路の実行回数は `shot_count` で指定されます。

回路の測定結果のヒストグラムとシミュレーションの実行時間（ミリ秒単位）またはエラーメッセージを返します。

`circuit` が無効な場合、それはホストに送信されず、エラーがスローされます。`circuit` が無効である理由は以下の通りです：

  * `circuit` に `Readout` 命令が含まれていない（[`CircuitContainsAReadoutTranspiler`](@ref) を参照）。
  * 複数の `Readout` 命令が同じ宛先ビットを持っている（[`ReadoutsDoNotConflictTranspiler`](@ref) を参照）。
  * `Readout` 命令が各量子ビットの最後の操作でない（[`ReadoutsAreFinalInstructionsTranspiler`](@ref) を参照）。
  * `circuit` に二つ以上の量子ビットで動作する `Controlled` ゲートが含まれている（[`UnsupportedGatesTranspiler`](@ref) を参照）。

# 例

```jldoctest
julia> qpu = AnyonYukonQPU(client, "project_id")
Quantum Processing Unit:
   manufacturer:  Anyon Systems Inc.
   generation:    Yukon
   serial_number: ANYK202201
   project_id:    project_id
   qubit_count:   6 
   connectivity_type:  linear
   realm:         test-realm

julia> circuit = QuantumCircuit(
            qubit_count = 3,
            instructions = [sigma_x(3), control_z(2, 1), readout(1, 1)]
        );

julia> run_job(qpu, circuit, 100)
(Dict("001" => 100), 542)

```
