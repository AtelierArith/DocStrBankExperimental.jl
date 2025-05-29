```
new_canvas(renderer::Renderer)
new_canvas(renderer::Renderer, figure::Figure)
new_canvas(renderer::Renderer, axis::Axis)
new_canvas(renderer::Renderer, gridpos::GridPosition)
```

`renderer`によって使用される新しい[`Canvas`](@ref)を作成します。新しいキャンバスのベースとして使用する既存の`figure`、`axis`、または`gridpos`を指定できます。
