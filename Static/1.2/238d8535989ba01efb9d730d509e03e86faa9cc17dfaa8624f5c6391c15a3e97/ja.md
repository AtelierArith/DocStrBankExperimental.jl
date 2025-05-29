```
StaticInt(N::Int) -> StaticInt{N}()
```

静的サイズの `Int`。数値のように振る舞わせたい場合は、`Val(N)` の代わりに `StaticInt(N)` を使用してください。
