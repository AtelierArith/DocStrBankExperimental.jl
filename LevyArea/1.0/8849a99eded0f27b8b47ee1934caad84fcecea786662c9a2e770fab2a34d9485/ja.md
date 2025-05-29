```
iterated_integrals(W::AbstractVector, q_12::AbstractVector, h, eps; 
    ito_correction=true,
    error_norm=FrobeniusL2(),
    alg=optimal_algorithm(length(W),q_12,h,eps,error_norm)
)
```

有限次元のQ-ウィーナー過程の反復確率積分の近似をシミュレートします。共分散行列は$Q = Q^\frac{1}{2}*Q^\frac{1}{2}$です。ここで`q_12`は$Q^\frac{1}{2}$の固有値のベクトルであり、共分散行列の平方根です。同様に、これらは$Q$の固有値の平方根です。

# 例

```jldoctest; setup=:(using LinearAlgebra; using LevyArea)
julia> h = 0.01; dim=10; q = [1/k^2 for k=1:dim];

julia> W = √h * sqrt.(q) .* randn(dim);

julia> diag(iterated_integrals(W,sqrt.(q),h,h^(3/2))) ≈ 0.5*W.^2 .- 0.5*h*q
true
```
