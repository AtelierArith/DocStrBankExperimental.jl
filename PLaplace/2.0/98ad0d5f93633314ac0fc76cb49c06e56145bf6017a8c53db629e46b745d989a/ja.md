```
objective_functional(
    u::AbstractVector{Float64},
    p::Float64,
    mesh::Mesh; 
    f::Union{AbstractVector{Float64}, Function, Missing} = missing,
    neumann_boundary::Union{Set{Boundary}, Set{Int64}, Missing} = missing,
    h::Union{AbstractVector{Float64}, Function, Missing} = missing,
    qdim::Int64 = 1
) -> Float64
```

uで評価されたp-Laplace問題の変分定式関数の値を返します。
