```
function FixedDofs(unknown_id::Int, value::Real; name::String = "")
```

は、FixedDofs 制約を構築します。これは（PDEDescription に割り当てられた場合）、dofs が指定された値に固定されることを保証します。
