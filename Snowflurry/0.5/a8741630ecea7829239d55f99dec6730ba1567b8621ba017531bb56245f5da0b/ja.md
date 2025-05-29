```
transpile_and_run_job(
    qpu::VirtualQPU,
    circuit::QuantumCircuit,
    shot_count::Integer;
    transpiler::Transpiler = get_transpiler(qpu)
)
```

このメソッドは、デフォルトのトランスパイラまたはキーワード引数として渡された他のトランスパイラを使用して、入力回路を最初にトランスパイルします。トランスパイルされた回路は、`QPU`シミュレーター上で実行され、回路の実行回数は`shot_count`で指定されます。

回路の測定結果のヒストグラム、またはエラーメッセージを返します。

# 例

```jldoctest; filter =  r", [0-9]+" => ", 132"
julia> qpu = VirtualQPU();

julia> circuit = QuantumCircuit(
                    qubit_count = 3,
                    instructions = [
                        sigma_x(3),
                        control_z(2, 1),
                        readout(1, 1),
                        readout(2, 2),
                        readout(3, 3)
                    ]);

julia> transpile_and_run_job(qpu, circuit,100)
(Dict("001" => 100), 132)

```
