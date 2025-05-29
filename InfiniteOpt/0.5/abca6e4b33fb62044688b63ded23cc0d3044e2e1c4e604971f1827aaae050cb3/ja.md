```
delete_domain_restrictions(cref::InfOptConstraintRef)::Nothing
```

制約 `cref` のすべてのドメイン制限を削除します。`cref` 内の有限変数に必要な制限は影響を受けません。

**例**

```julia-repl
julia> @constraint(model, c1, y <= 42, DomainRestrictions(x => 0))
c1 : y(x) ≤ 42, ∀ x[1] = 0, x[2] = 0

julia> delete_domain_restrictions(c1)

julia> c1
c1 : y(x) ≤ 42, ∀ x[1] ∈ [-1, 1], x[2] ∈ [-1, 1]
```
