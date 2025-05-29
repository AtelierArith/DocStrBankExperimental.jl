```
partial_copy(pso::PSOModel{T, U};
    Y::Union{Vector{V}, Nothing}=nothing,
    P::Union{V, Nothing}=nothing,
    Q::Union{V, Nothing}=nothing,
    ports::Union{AbstractVector{W}, Nothing}=nothing) where {T, U, V, W}

partial_copy(bbox::Blackbox{T, U};
    Y::Union{Vector{V}, Nothing}=nothing,
    P::Union{V, Nothing}=nothing,
    Q::Union{V, Nothing}=nothing,
    ports::Union{AbstractVector{W}, Nothing}=nothing) where {T, U, V, W}
```

キーワード引数として与えられたフィールドを除いて、同じフィールドを持つ新しいモデルを作成します。
