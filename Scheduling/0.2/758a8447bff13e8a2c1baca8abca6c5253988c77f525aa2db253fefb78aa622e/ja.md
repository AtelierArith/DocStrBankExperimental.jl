```
Jobs(P::Array{Int, 1})
```

`P` 配列によって決定される基本処理時間を持つジョブのセットを生成します。ジョブは `J_1`、`J_2` などと表されます。

# 例

```julia-repl
julia> Jobs([1, 5, 6, 2])
A set of 4 job(s):
    Job J_1:    [p = 1]
    Job J_2:    [p = 5]
    Job J_3:    [p = 6]
    Job J_4:    [p = 2]

```
