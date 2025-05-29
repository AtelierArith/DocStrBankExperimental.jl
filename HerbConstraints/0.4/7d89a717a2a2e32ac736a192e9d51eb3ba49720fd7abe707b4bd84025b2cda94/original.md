```
substitute!(solver::GenericSolver, path::Vector{Int}, new_node::AbstractRuleNode; is_domain_increasing::Union{Nothing, Bool}=nothing)
```

Substitute the node at the `path`, with a `new_node`.

  * `is_domain_increasing`: indicates if all grammar constraints should be repropagated from the ground up.

Domain increasing substitutions are substitutions that cannot be achieved by repeatedly removing values from domains. Example of an domain increasing event: `hole[{3, 4, 5}] -> hole[{1, 2}]`. Example of an domain decreasing event: `hole[{3, 4, 5}] -> rulenode(4, [hole[{1, 2}], rulenode(1)])`.
