```
RedPitayaCluster(hosts::Vector{String} [, port = 5025])
```

`RedPitayaCluster`を構築します。

構築中に最初のホストはクラスターのマスターRedPitayaとしてラベル付けされ、すべてのRedPitayaは`EXTERNAL`トリガーモードを使用するように設定されます。

詳細は[`RedPitaya`](@ref)、[`master`](@ref)を参照してください。

# 例

```julia
julia> rpc = RedPitayaCluster(["192.168.1.100", "192.168.1.101"]);

julia> rp = master(rpc)

julia> rp == rpc[1]
true
```
