```
remove_edges!(sim::Simulation, to::AgentID, ::Type{E})
```

`to`がターゲット位置にあるとき、タイプ`E`のすべてのエッジを削除します。

`E`が`write`引数にあり、[`apply!`](@ref)の`add_existing`リストにもある場合にのみ、遷移関数内で呼び出すことができます。
