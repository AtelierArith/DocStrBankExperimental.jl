```
Sync(assets...)
```

ブラウザで順次（同期的に）インポートされる資産のグループ（「ブロック」）。これは、依存関係に順番に実行する必要がある副作用がある場合に便利です。`assets`の要素は、[`Asset`](@ref)自体、[`Asset`](@ref)の有効なコンストラクタ、または[`Sync`](@ref)または[`Async`](@ref)のいずれかである可能性があります。

インポートが順次行う必要がない場合は、代わりに[`Async`](@ref)を使用してください。

# 例

```julia-repl
julia> WebIO.Sync(Asset("foo.js"), "bar" => "bar.js")
Sync(Asset[Asset("js", nothing, "foo.js"), Asset("js", "bar", "bar.js")])
```
