```
Machines(S::Array{Int, 1})
```

`S` 配列によって決定される速度を持つ機械のセットを生成します。これは `Q_1`、`Q_2` などで示されます。

# 例

```julia-repl
julia> Machines([1, 3, 2])
A set of 3 machine(s):
    Machine Q_1
    Machine Q_2:     [s = 3]
    Machine Q_3:     [s = 2]

```
