For a not-necessarily-minimal generating set, return the minimal generating set.

The input has to have only real phases.

```jldoctest
julia> minimal_generating_set(S"__ XZ ZX YY")
+ XZ
+ ZX
```
