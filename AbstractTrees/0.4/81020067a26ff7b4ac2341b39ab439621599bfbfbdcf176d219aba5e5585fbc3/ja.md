```
repr_tree(tree; context=nothing, kw...)
repr_tree(f, tree; context=nothing, kw...)
repr_tree(f, g, tree; context=nothing, kw...)
```

渡された引数で[`print_tree`](@ref)を呼び出した結果の文字列を取得します。

`context`引数は`Base.repr`と同様に機能します。
