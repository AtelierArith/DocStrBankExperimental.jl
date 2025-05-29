```
JuMP.build_constraint(_error::Function, func, set,
                      restrictions::DomainRestrictions{GeneralVariableRef}
                      )::DomainRestrictedConstraint
```

Extend `JuMP.buid_constraint` to handle including `restrictions` to its inherit  infinite parameter domains in addition to the traditional `func` in `set` setup.  This returns a `DomainRestrictedConstraint` that can then  be added via `JuMP.add_constraint`. Errors if the restrictions are incompadible  with infinite parameter domains. 

**Example**

```julia-repl
julia> restrictions = DomainRestrictions(t => 0)
Subdomain restrictions (1): t = 0

julia> con = build_constraint(error, y + 2, MOI.LessThan(0.0), restrictions);
```
