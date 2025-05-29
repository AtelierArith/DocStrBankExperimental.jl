```
DomainRestrictions{P <: GeneralVariableRef}
```

A `DataType` for storing interval domains that constrain particular infinite  parameters to a subdomain relative to their full domain. This is used to define subdomains of [`DomainRestrictedConstraint`](@ref)s. Note that the GeneralVariableRef must pertain to infinite parameters.

The constructor syntax is

```julia
DomainRestrictions(restrictions...)
```

where each argument of `restrictions` is one of the following forms:

  * `pref => value`
  * `pref => [lb, ub]`
  * `pref => IntervalDomain(lb, ub)`
  * `prefs => value`
  * `prefs => [lb, ub]`
  * `prefs => IntervalDomain(lb, ub)`.

Note that `pref` and `prefs` must correspond to infinite parameters. 

**Fields**

  * `intervals::Dict{GeneralVariableRef, IntervalDomain}`: A dictionary of interval bounds on infinite parameters.
