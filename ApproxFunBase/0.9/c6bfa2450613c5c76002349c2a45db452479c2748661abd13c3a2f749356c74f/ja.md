```
λ, V = eigs(BC::Operator, A::Operator, n::Integer; tolerance::Float64=100eps())
```

演算子 `A` の `n` 個の固有値と固有ベクトルを、境界条件 `BC` に従って計算します。

# 例

```jldoctest
julia> #= 我々はゼロ境界条件に従って、
          二次導関数のスペクトルを計算します。
          チェビシェフ基底でこの固有値問題を解きます =#

julia> S = Chebyshev();

julia> D = Derivative(S, 2);

julia> BC = Dirichlet(S);

julia> λ, v = ApproxFun.eigs(BC, D, 100);

julia> λ[1:10] ≈ [-(n*pi/2)^2 for n in 1:10] # 解析結果と比較
true
```
