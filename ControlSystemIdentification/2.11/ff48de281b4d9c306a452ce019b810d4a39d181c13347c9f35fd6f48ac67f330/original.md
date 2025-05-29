```
find_similarity_transform(sys1, sys2, method = :obsv)
```

Find T such that `ControlSystemsBase.similarity_transform(sys1, T) == sys2`

Ref: Minimal state-space realization in linear system theory: an overview, B. De Schutter

If `method == :obsv`, the observability matrices of `sys1` and `sys2` are used to find `T`, whereas `method == :ctrb` uses the controllability matrices.

```jldoctest
julia> T = randn(3,3);

julia> sys1 = ssrand(1,1,3);

julia> sys2 = ControlSystemsBase.similarity_transform(sys1, T);

julia> T2 = find_similarity_transform(sys1, sys2);

julia> T2 ≈ T
true
```
