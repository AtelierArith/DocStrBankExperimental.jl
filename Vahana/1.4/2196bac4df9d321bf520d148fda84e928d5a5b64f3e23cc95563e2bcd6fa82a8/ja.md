```
add_raster!(sim, name::Symbol, dims::NTuple{N, Int}, agent_constructor)
```

`sim`にn次元グリッドを追加し、次元は`dims`です。

各セルには新しいノード/エージェントがグラフに追加されます。エージェントを作成するために、セルの位置を`CartesianIndex`の形で引数として持つ`agent_constructor`関数が呼び出されます。

シンボル`name`は作成されたラスタの識別子であり、`sim`に複数のラスタを追加することが許可されています。

`agent_constructor`によって作成されるエージェントの型は、すでに[`register_agenttype!`](@ref)を介して登録されている必要があります。

作成されたエージェントのIDを含むベクターを返します。

[`finish_init!`](@ref)の前にのみ呼び出すことができます。

他にも[`calc_raster`](@ref)、[`connect_raster_neighbors!`](@ref)、および[`move_to!`](@ref)を参照してください。
