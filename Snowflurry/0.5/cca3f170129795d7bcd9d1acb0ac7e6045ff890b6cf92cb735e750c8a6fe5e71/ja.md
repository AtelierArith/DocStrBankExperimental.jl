```
run_job(qpu::VirtualQPU, circuit::QuantumCircuit, shot_count::Integer)
```

`QPU`シミュレーター上で回路を実行します。回路の実行回数は`shot_count`で指定されます。

回路の測定結果のヒストグラムを、`circuit`内の`Readout`命令に従って返します。

# 例

```jldoctest; filter =  r", [0-9]+" => ", 147"
julia> qpu = VirtualQPU();

julia> circuit = QuantumCircuit(
            qubit_count = 3,
            instructions = [
                sigma_x(3),
                control_z(2, 1),
                readout(1, 1),
                readout(2, 2),
                readout(3, 3)
            ]
        );

julia> run_job(qpu, circuit, 100)
(Dict("001" => 100), 147)

```
