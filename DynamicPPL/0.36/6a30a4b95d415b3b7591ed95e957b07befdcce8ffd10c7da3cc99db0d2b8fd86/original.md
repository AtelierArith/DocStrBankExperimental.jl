```
ConditionContext{Values<:Union{NamedTuple,AbstractDict},Ctx<:AbstractContext}
```

Model context that contains values that are to be conditioned on. The values can either be a NamedTuple mapping symbols to values, such as `(a=1, b=2)`, or an AbstractDict mapping varnames to values (e.g. `Dict(@varname(a) => 1, @varname(b) => 2)`). The former is more performant, but the latter must be used when there are varnames that cannot be represented as symbols, e.g. `@varname(x[1])`.
