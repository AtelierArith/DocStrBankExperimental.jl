```
render_trajectory(renderer::Renderer,
                  domain::Domain, trajectory::AbstractVector{<:State})
```

`renderer`を使用してPDDL `domain`状態の`trajectory`をレンダリングします。新しい[`Canvas`](@ref)を構築して返します。
