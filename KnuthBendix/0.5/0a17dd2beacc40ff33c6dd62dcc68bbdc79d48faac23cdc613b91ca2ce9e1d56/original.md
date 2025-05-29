```
knuthbendix(rws::AbstractRewritingSystem)
knuthbendix(settings::Settings, rws::AbstractRewritingSystem)
```

Perform Knuth-Bendix completion on rewriting system `rws` using algorithm defined by `method`.

!!! warn
    Rewriting systems returned by the completion algorithm may not be confluent. Usually this happens when

      * number of rules stored in `rws` exceeds the one permitted in `settings`,
      * the completion process is manually interrupted,
      * or when the `settings` allow the algorithm to skip the processing of certain critical pairs.

    You should always assume that the rewriting system is **not** confluent, unless [`isconfluent`](@ref) returns `true`.


Unless manually interrupted the returned rewriting system will be reduced.
