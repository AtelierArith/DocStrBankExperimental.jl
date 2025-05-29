```
add_agent!(agent::AbstractAgent [, pos], model::ABM) → agent
```

指定された位置に`agent`をモデルに追加します。`pos`が指定されていない場合、`agent`はランダムな位置に追加されます。`agent`の位置は常に`position`に合わせて更新されるため、`add_agent!`において`agent`の位置は意味を持ちません。`agent`の位置を使用するには[`add_agent_own_pos!`](@ref)を使用してください。`pos`の型は基盤となる空間の位置型と一致する必要があります。
