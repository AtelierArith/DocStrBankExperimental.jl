```
optimal_algorithm(dim, stepsize, eps=stepsize^(3/2), norm=MaxL2())
optimal_algorithm(dim, q_12, stepsize, eps, norm=FrobeniusL2())
```

与えられたパラメータに対して最適なアルゴリズムを返します。つまり、所望の精度 `eps` を達成するために必要なランダム数のシミュレーションが最も少ないアルゴリズムです。

# 例

```jldoctest; setup=:(using LevyArea)
julia> h = 1/128;

julia> optimal_algorithm(10, h, h^(3/2), MaxL2())
MronRoe()

julia> optimal_algorithm(10, 1.0./(1:10).^2, h, h^(3/2), FrobeniusL2())
Milstein()
```
