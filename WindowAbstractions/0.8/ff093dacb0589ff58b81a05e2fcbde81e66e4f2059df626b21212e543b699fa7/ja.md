ポインタの動作が行われたコンテキスト、アクティブなマウスボタンとキーボード修飾子を含む。

```julia
struct PointerState
```

  * `state::WindowAbstractions.MouseButton`
  * `modifiers::WindowAbstractions.ModifierState`
