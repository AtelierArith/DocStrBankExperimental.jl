```
get_status(client::Client,circuitID::String)::Tuple{Status,Dict{String,Int}}
```

`client`を使用して`QPU`サービスに接続し、回路計算のステータスを取得します。可能なステータスの詳細については、[`Status`](@ref)を参照してください。

status["type"]が"FAILED"の場合、サーバーエラーはstatus["message"]に含まれています。

status["type"]が"SUCCEEDED"の場合、返されるタプルの2番目の要素は`QPU`上で計算されたジョブ結果のヒストグラムであり、3番目の要素は`QPU`上でのジョブの実行時間（ミリ秒単位）です。

# 例

```jldoctest
julia> circuit = QuantumCircuit(
            qubit_count = 3,
            instructions = [sigma_x(3), control_z(2, 1),
            readout(1, 1)]
        );

julia> jobID = submit_job(submit_job_client, circuit, 100, "project_id", "yukon")
"8050e1ed-5e4c-4089-ab53-cccda1658cd0"

julia> get_status(submit_job_client, jobID)
(Status: SUCCEEDED
, Dict("001" => 100), 542)

```
