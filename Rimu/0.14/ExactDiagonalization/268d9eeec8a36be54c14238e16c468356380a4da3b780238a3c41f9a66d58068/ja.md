```
solve(p::ExactDiagonalizationProblem, [algorithm]; kwargs...)
```

[`ExactDiagonalizationProblem`](@ref) `p`を直接解きます。オプションで`algorithm`を指定できます。固有値、固有ベクトル、および収束情報を含む結果タイプを返します。

キーワード引数の説明については、[`ExactDiagonalizationProblem`](@ref)のドキュメントを参照してください。

また、[`solve(::ProjectorMonteCarloProblem)`](@ref CommonSolve.solve(::ProjectorMonteCarloProblem))も参照してください。
