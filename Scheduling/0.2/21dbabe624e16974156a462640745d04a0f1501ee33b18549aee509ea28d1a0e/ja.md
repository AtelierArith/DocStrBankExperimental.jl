```
Jobs(P::Array{Rational{Int}, 1})
```

基本的な処理時間が `P` 配列によって決定されるジョブのセットを生成します。ジョブは `J_1`、`J_2` などと表されます。

# 例

```julia-repl
julia> Jobs([1//2, 3, 5//3, 7])
A set of 4 job(s):
​    Job J_1:    [p = 1//2]
    Job J_2:    [p = 3]
    Job J_3:    [p = 5//3]
    Job J_4:    [p = 7]

```
