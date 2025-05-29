```
by_name(agent, name::Union{Glob.FilenameMatch, Regex})
```

階層内のエージェントを返し、その名前が指定されたワイルドカードと一致します。`inners_only==true` の場合、`agent` の子孫のみを考慮します。
