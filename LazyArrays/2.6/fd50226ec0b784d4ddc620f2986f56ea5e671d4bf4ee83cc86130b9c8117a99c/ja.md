```
@~ expr
```

`Broadcasted` または `Applied` オブジェクトを作成するためのマクロです。`expr` 内の `f(args...)` のような通常の呼び出しは `applied(f, args...)` に置き換えられます。`expr` 内の `f(args...)` のようなドット呼び出しは `broadcasted.(f, args...)` に置き換えられます。配列ベースのインターフェースが必要な場合は `LazyArray(@~ expr)` を使用してください。

```
julia> @~ A .+ B ./ 2

julia> @~ @. A + B / 2

julia> @~ A * B + C
```
