```
register(
container,
agent,
suggested_aid::Union{String,Nothing}=nothing;
kwargs...,
```

)

エージェントをコンテナに登録します。便利のためにエージェント自体を返します。

通常、支援は生成されますが、支援を提案することも可能であり、まだ使用されていない場合やデフォルトの命名パターン（agent0、agent1、...）と衝突しない場合に使用されます。
