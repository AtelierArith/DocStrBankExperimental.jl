```
id_in_position(pos, model::ABM{<:GridSpaceSingle}) → id
```

指定された位置にいるエージェントのIDを返します。この位置にエージェントがいない場合は `0` になります。

これは [`ids_in_position`](@ref) に似ていますが、`GridSpaceSingle` に特化しています。さらに [`isempty`](@ref) も参照してください。
