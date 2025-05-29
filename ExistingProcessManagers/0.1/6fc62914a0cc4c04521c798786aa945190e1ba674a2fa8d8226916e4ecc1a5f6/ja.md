```
parse_julia_worker_output_to_hosts_and_ports(; regex = julia_worker_regex)
```

Julia ワーカーによって出力された内容を解析し、ホストとポートのリストを返します。

## 例

```jldoctest; setup = :(using ExistingProcessManagers; using Distributed)
julia> worker_output = """
       julia_worker:9960#192.168.1.151
       julia_worker:9962#192.168.1.153
       julia_worker:9964#192.168.1.155
       julia_worker:9966#192.168.1.157
       julia_worker:9968#192.168.1.159
       """;

julia> hosts_and_ports = parse_julia_worker_output_to_hosts_and_ports(worker_output);
```

次に、以下の2つのオプションのいずれかを実行できます。どちらも同等です。

オプション 1:

```julia
julia> addprocs(ExistingProcessManager(hosts_and_ports))
```

オプション 2:

```julia
julia> addprocs_existing(hosts_and_ports)
```
