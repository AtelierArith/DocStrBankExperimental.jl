```
ExistingProcessManager(worker_output::AbstractString)
```

Julia ワーカープロセスによって印刷された出力から `ExistingProcessManager` を構築します。

## 例

```jldoctest; setup = :(using ExistingProcessManagers; using Distributed)
julia> worker_output = """
       julia_worker:9960#192.168.1.151
       julia_worker:9960#192.168.1.151
       julia_worker:9960#192.168.1.151
       julia_worker:9966#192.168.1.157
       julia_worker:9968#192.168.1.159
       """;

julia> manager = ExistingProcessManager(worker_output);
```

これで次のことができます：

```julia
julia> addprocs(manager)
```
