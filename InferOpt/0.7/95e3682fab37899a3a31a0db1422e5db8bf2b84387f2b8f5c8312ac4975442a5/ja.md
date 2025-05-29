```julia
LinearMaximizer(
    maximizer;
    g,
    h
) -> InferOpt.LinearMaximizer{_A, typeof(InferOpt.identity_kw), ComposedFunction{typeof(zero), typeof(InferOpt.eltype_kw)}} where _A

```

[`LinearMaximizer`](@ref) のコンストラクタ。
