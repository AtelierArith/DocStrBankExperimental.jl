```
JuMP.solver_name(model::InfiniteModel)
```

`solver_name`を拡張して、選択された最適化手法があり、それに名前属性がある場合は使用されているソルバーの名前を返すようにします。そうでない場合は、エラーがスローされます。

**例**

```julia-repl
julia> solver_name(model)
"Gurobi"
```
