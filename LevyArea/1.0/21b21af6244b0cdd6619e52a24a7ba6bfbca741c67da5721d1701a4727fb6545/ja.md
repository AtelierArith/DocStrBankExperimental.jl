```
iterated_integrals(W::AbstractVector, h, eps=h^(3/2);
    ito_correction=true,
    error_norm=MaxL2(),
    alg=optimal_algorithm(length(W),h,eps,error_norm)
)
```

与えられた $m$ 次元ブラウン運動のすべてのペア $1\le i, j \le m$ に対して、反復確率積分 $\int_0^h\int_0^sdW_i(t)dW_j(s)$ の近似をシミュレートします。ステップサイズは h です。

# 例

```jldoctest; setup=:(using LinearAlgebra; using LevyArea)
julia> h = 1/2;

julia> W = [1.0, 0.5]
2-element Vector{Float64}:
 1.0
 0.5

julia> diag(iterated_integrals(W, h, h^(3/2))) ≈ 0.5*W.^2 .- 0.5h
true
```
