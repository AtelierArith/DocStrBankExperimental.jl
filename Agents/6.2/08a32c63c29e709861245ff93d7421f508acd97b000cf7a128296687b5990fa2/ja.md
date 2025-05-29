```
map_agent_groups(order::Int, f::Function, model::ABM; kwargs...)
map_agent_groups(order::Int, f::Function, model::ABM, filter::Function; kwargs...)
```

関数 `f` を [`iter_agent_groups`](@ref) イテレータのすべてのグループ化されたエージェントに適用します。 `kwargs` はイテレータメソッドに渡されます。 `f` は `f(NTuple{O,AgentType})` の形式を取る必要があり、次元 `O` は `order` に等しいです。

オプションとして、反復可能な引数を受け取り、`Bool` を返す `filter` 関数を適用して、結果から不要な一致を削除することができます。 **注意:** このオプションは行列の順序を保持できないため、エージェントIDを結果データに関連付けるために [`index_mapped_groups`](@ref) と併用して使用する必要があります。
