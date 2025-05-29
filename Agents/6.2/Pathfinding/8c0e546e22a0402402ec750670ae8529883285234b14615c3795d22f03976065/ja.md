```
plan_best_route!(agent, dests, pathfinder::AStar{D}; kwargs...)
```

エージェントを現在の位置から `dests` から選択した目的地まで移動させるための最適な経路を計算、保存、返します。

`condition = :shortest` キーワードは、可能な目的地の中で最も短い経路を返します。代わりに、`:longest` 経路も要求することができます。

選択した目的地の位置を返します。提供された目的地のいずれも到達可能でない場合は `nothing` を返します。
