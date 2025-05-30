```
submit_job(
    client::Client,
    circuit::QuantumCircuit,
    shot_count::Integer,
    project_id::String,
    machine_name::String
)
```

`client`を使用して、ホストサーバー上のQPUサービスに`circuit`を送信します。QPUサービスは`machine_name`で指定されます。回路の実行回数は`shot_count`で指定されます。

回路IDを返します。これは、[`get_status`](@ref)を呼び出す際に使用できます。

# 例

```jldoctest mylabel
julia> circuit = QuantumCircuit(
            qubit_count = 3,
            instructions = [sigma_x(3), control_z(2, 1),
            readout(1, 1)]
        );

julia> submit_job(client, circuit, 100, "project_id", "yukon")
"8050e1ed-5e4c-4089-ab53-cccda1658cd0"

```
