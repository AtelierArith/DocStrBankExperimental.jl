```
fit(::Type{RationalFunction}, xs::AbstractVector{S}, ys::AbstractVector{T}, m, n; var=:x)
```

データ `(x,y)` に対して、形式 `pq = (a₀ + a₁x¹ + … + aₘxᵐ) / (1 + b₁x¹ + … + bₙxⁿ)` の有理関数をフィットさせます。

!!! note
    これは、非線形最小二乗問題を解くためにガウス・ニュートン法の簡単な実装を使用します: `minᵦ Σ(yᵢ - pq(xᵢ,β)²`、ここで `β=(a₀,a₁,…,aₘ,b₁,…,bₙ)` です。

    より迅速に収束する方法は `LsqFit.jl` パッケージで使用されており、パフォーマンスが重要な場合は、そのパッケージで使用するために問題を再表現することが推奨されます。

    さらに、適応的な次数の正確な有理関数フィットに関心がある場合、`BaryRational.jl` パッケージは AAA アルゴリズムの実装を提供します（"他のアルゴリズムでは見られない速度、柔軟性、堅牢性を提供します" [Nakatsukasa, Sète, Trefethen](https://arxiv.org/pdf/1612.00337.pdf)）および Floater-Hormann 重みを使用したもの [Floater, Hormann](https://doi.org/10.1007/s00211-007-0093-y)（"実際の極がなく、点の分布に関係なく任意の実区間で非常に高い近似次数を持つ"）

    [RationalApproximations](https://github.com/billmclean/RationalApproximations) パッケージにも AAA アルゴリズムの実装があります。

    Python ライブラリ [polyrat](https://github.com/jeffrey-hokanson/polyrat) には他のアルゴリズムの実装があります。


## 例

```julia-repl
julia> x = variable(Polynomial{Float64})
Polynomial(1.0*x)

julia> pq = (1+x)//(1-x)
(1.0 + 1.0*x) // (1.0 - 1.0*x)

julia> xs = 2.0:.1:3;

julia> ys = pq.(xs);

julia> v = fit(RationalFunction, xs, ys, 2, 2)
(1.0 + 1.0*x - 6.82121e-13*x^2) // (1.0 - 1.0*x + 2.84217e-13*x^2)

julia> maximum(abs, v(x)-pq(x) for x ∈ 2.1:0.1:3.0)
1.06314956838105e-12

julia> using BaryRational

julia> u = aaa(xs,ys)
(::BaryRational.AAAapprox{Vector{Float64}}) (generic function with 1 method)

julia> maximum(abs, u(x)-pq(x) for x ∈ 2.1:0.1:3.0)
4.440892098500626e-16

julia> u(variable(pq)) # 使用される多項式を確認するため
(2.68328 + 0.447214*x - 1.78885*x^2 + 0.447214*x^3) // (2.68328 - 4.91935*x + 2.68328*x^2 - 0.447214*x^3)
```
