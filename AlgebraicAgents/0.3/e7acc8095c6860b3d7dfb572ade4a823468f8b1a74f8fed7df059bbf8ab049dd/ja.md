```
by_name(agent, name::AbstractString; inners_only=false)
```

与えられた `name` を持つ階層内のエージェントを返します。`inners_only==true` の場合、`agent` の子孫のみを考慮します。
