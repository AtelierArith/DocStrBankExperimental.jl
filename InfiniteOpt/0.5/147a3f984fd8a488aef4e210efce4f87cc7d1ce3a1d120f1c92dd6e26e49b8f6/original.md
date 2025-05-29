```
DomainRestrictedConstraint{C <: JuMP.AbstractConstraint, 
                           P <: GeneralVariableRef
                           } <: JuMP.AbstractConstraint
```

A `DataType` for creating a constraint with enforced `DomainRestrictions`. For  example this may pertain to a boundary condition.

**Fields**

  * `constraint::C`: The optimization constraint.
  * `restrictions::DomainRestrictions{P}`: The restrictions that determine the   sub-domain of the constraint.
