```
不連続
```

不連続に使用される制約のタグとして使用されます。これは次の構文を介して行われます：

```julia-repl
julia> @constraint(model, [constr_expr], Disjunct)

julia> @constraint(model, [constr_expr], Disjunct(lvref))
```

ここで `lvref` は、制約が追加される不連続に最終的に関連付けられる [`LogicalVariableRef`](@ref) です。`lvref` が指定されていない場合、不連続が作成されるときに1つが生成されます。
