```
solve(::DirichletProblem{<:DiffusionEquation{1}}, ::MathiasAndSander[; maxiters]) -> Solution
```

MathiasとSander（2021）の擬似スペクトル法を使用してディリクレ問題を解きます。

# キーワード引数

  * `maxiters=100`: 最大反復回数。

# 参考文献

MATHIAS, S. A.; SANDER, G. C. 擬似スペクトル法は水平浸透方程式に対して迅速かつ正確な解を提供します。水文学ジャーナル, 2021, vol. 598, p. 126407。

参照：[`MathiasAndSander`](@ref), [`Solution`](@ref)
