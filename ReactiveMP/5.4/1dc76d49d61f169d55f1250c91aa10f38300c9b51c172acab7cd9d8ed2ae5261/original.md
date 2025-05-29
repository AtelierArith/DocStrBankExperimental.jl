```
marginalrule(fform, on, mnames, messages, qnames, marginals, meta, __node)
```

This function is used to compute a local joint marginal for a given node

# Arguments

  * `fform`: Functional form of the node in form of a type of the node, e.g. `::Type{ <: NormalMeanVariance }` or `::typeof(+)`
  * `on`: Local joint marginal tag , e.g. `::Val{ :mean_precision }` or `::Val{ :out_mean_precision }`
  * `mnames`: Ordered messages names in form of the Val type, eg. `::Val{ (:mean, :precision) }`
  * `messages`: Tuple of message of the same length as `mnames` used to compute an outbound message
  * `qnames`: Ordered marginal names in form of the Val type, eg. `::Val{ (:mean, :precision) }`
  * `marginals`: Tuple of marginals of the same length as `qnames` used to compute an outbound message
  * `meta`: Extra meta information
  * `__node`: Node reference

See also: [`rule`](@ref), [`@rule`](@ref) [`@marginalrule`](@ref)
