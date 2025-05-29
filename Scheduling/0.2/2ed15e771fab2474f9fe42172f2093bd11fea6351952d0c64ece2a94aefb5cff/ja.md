```
Machines(S::Array{Rational{Int}, 1})
```

`S` 配列によって決定される速度を持つ機械のセットを生成します。これらは `Q_1`、`Q_2` などと表されます。

# 例

```julia-repl
julia> Machines([1, 1//2, 2])
A set of 3 machine(s):
    Machine Q_1
    Machine Q_2:     [s = 1//2]
    Machine Q_3:     [s = 2]

```
