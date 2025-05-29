```
is_positive(a::NumFieldElem, embs::Vector{NumFieldEmb}) -> Bool
```

Return whether the element $a$ is positive at all embeddings of `embs`. All embeddings in `embs` must be real.

```jldoctest
julia> K, a  = quadratic_field(5);

julia> e = complex_embedding(K, 2.1);

julia> e(a)
[2.236067977 +/- 5.02e-10]

julia> is_positive(a, [e])
true
```
