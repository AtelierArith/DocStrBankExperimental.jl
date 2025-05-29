```
rule(fform, on, vconstraint, mnames, messages, qnames, marginals, meta, __node)
```

This function is used to compute an outbound message for a given node

# Arguments

  * `fform`: Functional form of the node in form of a type of the node, e.g. `::Type{ <: NormalMeanVariance }` or `::typeof(+)`
  * `on`: Outbound interface's tag for which a message has to be computed, e.g. `::Val{:out}` or `::Val{:μ}`
  * `vconstraint`: Variable constraints for an outbound interface, e.g. `Marginalisation` or `MomentMatching`
  * `mnames`: Ordered messages names in form of the Val type, eg. `::Val{ (:mean, :precision) }`
  * `messages`: Tuple of message of the same length as `mnames` used to compute an outbound message
  * `qnames`: Ordered marginal names in form of the Val type, eg. `::Val{ (:mean, :precision) }`
  * `marginals`: Tuple of marginals of the same length as `qnames` used to compute an outbound message
  * `meta`: Extra meta information
  * `addons`: Extra addons information
  * `__node`: Node reference

For all available rules, see `ReactiveMP.print_rules_table()`.

See also: [`@rule`](@ref), [`marginalrule`](@ref), [`@marginalrule`](@ref)
