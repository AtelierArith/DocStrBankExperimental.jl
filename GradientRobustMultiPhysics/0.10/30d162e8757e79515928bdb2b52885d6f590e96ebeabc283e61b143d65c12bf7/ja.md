```julia
ConvectionRotationFormOperator(
    beta::Int64,
    beta_operator::Type{<:??},
    xdim::Int64,
    ncomponents::Int64;
    name,
    AT,
    factor,
    ansatz_operator,
    test_operator,
    regions
)

```

双線形形式 a(u,v) = (beta x curl(u),v) のコンストラクタであり、ここで beta は PDEDescription の未知のベクトル場の ID で、u と v もベクトル場であり、x は外積です（これまでのところ、これは 2D のみで実装されています）。
