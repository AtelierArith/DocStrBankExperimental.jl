```
hosts_and_ports_to_workerconfigs(hosts_and_ports::Vector{Tuple{String, Int}})
```

ホストとポート番号のリストを `WorkerConfig` のリストに変換します。

## 例

```jldoctest; setup = :(using ExistingProcessManagers; using Distributed)
julia> hosts_and_ports = [
       ("127.0.0.1", 9601), # ホストは "127.0.0.1" で、ポート番号は 9601
       ("127.0.0.1", 9602), # ホストは "127.0.0.1" で、ポート番号は 9602
       ];

julia> wconfigs = hosts_and_ports_to_workerconfigs(hosts_and_ports);
```

次の2つのオプションのいずれかを実行できます。どちらも同等です。

オプション 1:

```julia
julia> addprocs(ExistingProcessManager(wconfigs))
```

オプション 2:

```julia
julia> addprocs_existing(wconfigs)
```
