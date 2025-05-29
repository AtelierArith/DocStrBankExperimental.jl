```
JuMP.build_constraint(_error::Function, func, set,
                      restrictions::DomainRestrictions{GeneralVariableRef}
                      )::DomainRestrictedConstraint
```

`JuMP.buid_constraint`を拡張して、従来の`func`に加えて、無限パラメータドメインに`restrictions`を含めることができるようにします。これにより、`JuMP.add_constraint`を介して追加できる`DomainRestrictedConstraint`が返されます。制約が無限パラメータドメインと互換性がない場合はエラーが発生します。

**例**

```julia-repl
julia> restrictions = DomainRestrictions(t => 0)
Subdomain restrictions (1): t = 0

julia> con = build_constraint(error, y + 2, MOI.LessThan(0.0), restrictions);
```
