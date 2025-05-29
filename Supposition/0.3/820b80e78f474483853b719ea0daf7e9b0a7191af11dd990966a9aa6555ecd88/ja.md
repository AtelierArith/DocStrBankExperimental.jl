```
example(gen::Possibility, n::Integer; tries=100_000)
```

与えられた `Possibility` のために `n` の例を生成します。各例は生成するために `tries` 回の試行が与えられます。いずれかが失敗した場合、全体のプロセスは中止されます。

```julia-repl
julia> using Supposition, Supposition.Data

julia> is = Data.Integers(0, 10);

julia> example(is, 10)
10-element Vector{Int64}:
  9
  1
  4
  4
  7
  4
  6
 10
  1
  8
```
