```
render_sol!(canvas::Canvas, renderer::Renderer,
            domain::Domain, state::State, sol::Solution)
```

`renderer`を使用して、PDDL `domain`の`state`から始まる計画ソリューション`sol`をレンダリングします。既存のコンテンツの上に`canvas`にレンダリングします。
