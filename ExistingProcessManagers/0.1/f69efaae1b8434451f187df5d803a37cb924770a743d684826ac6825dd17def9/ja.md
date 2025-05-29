```
addprocs_existing(x; kwargs...)
```

`addprocs(ExistingProcessManager(x); kwargs...)` と同等です。

## 例

### 例 1

```julia
julia> hosts_and_ports = [
       ("127.0.0.1", 9601), # ホストは "127.0.0.1" で、ポート番号は 9601
       ("127.0.0.1", 9602), # ホストは "127.0.0.1" で、ポート番号は 9602
       ]
2-element Vector{Tuple{String, Int64}}:
 ("127.0.0.1", 9601)
 ("127.0.0.1", 9602)

julia> addprocs_existing(hosts_and_ports; kwargs...)
```

### 例 2

```julia
julia> w1 = WorkerConfig();

julia> w1.host = "127.0.0.1";

julia> w1.port = 9601;

julia> w2 = WorkerConfig();

julia> w2.host = "127.0.0.1";

julia> w2.port = 9602;

julia> wconfigs = WorkerConfig[w1, w2];

julia> addprocs_existing(wconfigs; kwargs...)
```

### 例 3

```julia
julia> worker_output = """
       julia_worker:9960#192.168.1.151
       julia_worker:9960#192.168.1.151
       julia_worker:9960#192.168.1.151
       julia_worker:9966#192.168.1.157
       julia_worker:9968#192.168.1.159
       """;

julia> addprocs_existing(worker_output; kwargs...)
```
