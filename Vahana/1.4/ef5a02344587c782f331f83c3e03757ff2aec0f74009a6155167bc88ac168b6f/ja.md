```
remove_edges!(sim::Simulation, from::AgentID, to::AgentID, ::Type{E})
```

エッジのソース位置に `from`、ターゲット位置に `to` があるタイプ `E` のすべてのエッジを削除します。この形の `remove_edges!`（引数として `from` を持つ）は、エッジタイプ `E` が `:IgnoreFrom` ヒントを持たない場合にのみ呼び出すことができます。

また、`E` が `write` 引数にあり、[`apply!`](@ref) の `add_existing` リストにも含まれている遷移関数内でのみ呼び出すことができます。
