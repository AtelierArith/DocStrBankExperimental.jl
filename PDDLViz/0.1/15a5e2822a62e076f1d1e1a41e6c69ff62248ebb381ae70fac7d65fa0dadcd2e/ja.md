```
render_sol(renderer::Renderer,
           domain::Domain, state::State, sol::Solution)
```

`renderer`を使用して、PDDL `domain`の`state`から始まる計画ソリューション`sol`をレンダリングします。新しい[`Canvas`](@ref)を構築して返します。
