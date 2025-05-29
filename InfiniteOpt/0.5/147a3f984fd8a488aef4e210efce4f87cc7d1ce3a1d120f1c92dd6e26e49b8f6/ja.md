```
DomainRestrictedConstraint{C <: JuMP.AbstractConstraint, 
                           P <: GeneralVariableRef
                           } <: JuMP.AbstractConstraint
```

`DomainRestrictions`が強制される制約を作成するための`DataType`です。例えば、これは境界条件に関係する場合があります。

**フィールド**

  * `constraint::C`: 最適化制約。
  * `restrictions::DomainRestrictions{P}`: 制約のサブドメインを決定する制限。
