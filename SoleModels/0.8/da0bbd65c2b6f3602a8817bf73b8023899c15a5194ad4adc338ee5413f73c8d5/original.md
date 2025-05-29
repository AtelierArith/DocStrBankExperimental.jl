```
rulemetrics(
    r::Rule,
    X::AbstractInterpretationSet,
    Y::AbstractVector{<:Label}
)
```

Compute metrics for a rule with respect to a labeled dataset and returns a `NamedTuple` consisting of:

  * `support`: number of instances satisfying the antecedent of the rule divided by   the total number of instances;
  * `error`:

      * For classification problems: number of instances that were not classified

    correctly divided by the total number of instances;

      * For regression problems: mean squared error;
  * `length`: number of atoms in the rule's antecedent.

See also [`Rule`](@ref), [`SoleLogics.AbstractInterpretationSet`](@ref), [`Label`](@ref), [`evaluaterule`](@ref), [`outcometype`](@ref), [`consequent`](@ref).
