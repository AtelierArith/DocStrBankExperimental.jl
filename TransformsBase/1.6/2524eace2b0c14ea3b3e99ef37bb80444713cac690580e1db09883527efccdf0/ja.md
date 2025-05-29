```
newobject = reapply(transform, object, cache)
```

以前の [`apply`](@ref) 呼び出しで作成された `cache` を使用して、（おそらく異なる）`object` に `transform` を再適用します。`cache` を使用せずに [`apply`](@ref) にフォールバックします。
