```
example(pos::Possibility; tries=100_000, generation::Int)
```

与えられた `Possibility` の例を生成します。

`example` は `pos` が `tries` 回例を生成することを試み、指定された時間内に `pos` が例を生成しない場合はエラーをスローします。`generation` は通常の `@check` の実行の中で例が生成された「遅さ」を示します。

使用法:

```julia-repl
julia> using Supposition, Supposition.Data

julia> example(Data.Integers(0, 10))
7
```
