```
ExistingProcessManager(hosts_and_ports::Vector{Tuple{String, Int}})
```

ホストとポート番号のリストから `ExistingProcessManager` を構築します。

## 例

```jldoctest; setup = :(using ExistingProcessManagers; using Distributed)
julia> hosts_and_ports = [
       ("127.0.0.1", 9601), # ホストは "127.0.0.1" で、ポート番号は 9601
       ("127.0.0.1", 9602), # ホストは "127.0.0.1" で、ポート番号は 9602
       ];

julia> manager = ExistingProcessManager(hosts_and_ports);
```

これで次のことができます：

```julia
julia> addprocs(manager)
```
