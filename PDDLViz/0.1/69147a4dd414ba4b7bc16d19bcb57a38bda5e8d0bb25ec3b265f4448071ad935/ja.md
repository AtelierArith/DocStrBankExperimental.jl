```
render_trajectory!(canvas::Canvas, renderer::Renderer,
                   domain::Domain, trajectory::AbstractVector{<:State})
```

`renderer`を使用して、PDDL `domain` 状態の `trajectory` をレンダリングします。既存のコンテンツの上に `canvas` にレンダリングします。
