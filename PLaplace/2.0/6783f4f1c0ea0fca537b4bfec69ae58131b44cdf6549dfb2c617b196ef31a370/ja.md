```julia
compute_errors(
    anasol::Vector{Float64},
    numsol::Vector{Float64},
    mesh::MinFEM.Mesh,
    neumann_boundary::Union{Missing, Set{Int64}, Set{MinFEM.Boundary}},
    h::Union{Missing, AbstractVector{Float64}},
    f::Union{Missing, AbstractVector{Float64}},
    p::Float64,
    qdim::Int64
) -> Vector{Float64}

```

与えられた離散化された解析解に対する数値解のさまざまな誤差を返します。最初の値は目的値の差における誤差であり、次に点ごとの誤差L1、L2、およびLInfノルムです。

離散化された解析解と数値解がメッシュと一致することを保証するためにラッパーを介して呼び出されることを意図しています。
