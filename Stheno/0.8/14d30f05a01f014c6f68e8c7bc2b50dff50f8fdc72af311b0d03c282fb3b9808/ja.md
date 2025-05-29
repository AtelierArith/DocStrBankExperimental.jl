```
stretch(f::AbstractGP, l::Union{AbstractVecOrMat{<:Real}, Real})
```

これは、プログラムに長さスケールを導入するための主要なメカニズムです。

`l isa Real` または `l isa AbstractMatrix{<:Real}` の場合、`stretch(f, l)(x) == f(l * x)` は任意の入力 `x` に対して成り立ちます。`l isa Real` の場合、これは長さスケールを `1 / l` でスケーリングすることに相当します。

`l isa AbstractVector{<:Real}` は `stretch(f, Diagonal(l))` に相当します。

`f ∘ Stretch(l)` に相当します。
