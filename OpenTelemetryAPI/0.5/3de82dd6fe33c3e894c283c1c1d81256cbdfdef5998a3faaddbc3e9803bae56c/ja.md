```
with_context(f, [context]; kv...)
```

関数 `f` を `context` 内で実行します。追加の `kv` ペアが提供されると、それらは `context` とマージされて新しいコンテキストが形成されます。`context` が提供されていない場合は、[`current_context`](@ref) が使用されます。
