## 概要

struct ExistingProcessManager <: Distributed.ClusterManager

## フィールド

  * wconfigs :: Vector{Distributed.WorkerConfig}

---

```
ExistingProcessManager(wconfigs::Vector{Distributed.WorkerConfig})
```

`WorkerConfig`のリストから`ExistingProcessManager`を構築します。

## 例

```jldoctest; setup = :(using ExistingProcessManagers; using Distributed)
julia> w1 = WorkerConfig();

julia> w1.host = "127.0.0.1";

julia> w1.port = 9601;

julia> w2 = WorkerConfig();

julia> w2.host = "127.0.0.1";

julia> w2.port = 9602;

julia> wconfigs = WorkerConfig[w1, w2];

julia> manager = ExistingProcessManager(wconfigs);
```

これで次のことができます：

```julia
julia> addprocs(manager)
```
