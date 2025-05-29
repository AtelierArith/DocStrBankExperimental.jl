```
Y = get_hessian(amp::AbstractManoptProblem{T}, p, X)
get_hessian!(amp::AbstractManoptProblem{T}, Y, p, X)
```

[`AbstractManoptProblem`](@ref) `amp` の点 `p` で接ベクトル `X` に適用されたヘッセ行列を評価し、$\operatorname{Hess}f(q)[X]$ を計算します。これは `Y` にインプレースで行うこともできます。
