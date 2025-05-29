```
mapinsertview(X; prop=f, ...)
```

`mapinsert`と同様ですが、コピーの代わりにビューを返します。

可能な場合（例えば`X isa StructArray`）：最適化されたアプローチを使用し、他のすべてのコンポーネントはそのまま保持します。
