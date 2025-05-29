```
sol = find_zero(
        f::F,
        method::RootSolvingMethod{FT},
        soltype::SolutionType,
        tol::Union{Nothing, AbstractTolerance} = nothing,
        maxiters::Int = 10_000,
        )
```

`f`の最も近い根を見つけます。`f(x) ≈ 0`となる根の値`x`と、収束を示すBoolean値`converged`を返します。

  * `f` は根を見つけるための方程式の関数
  * `method` は次のいずれかです：

      * `SecantMethod()`: [セカント法](https://en.wikipedia.org/wiki/Secant_method)
      * `RegulaFalsiMethod()`: [レグラファルシ法](https://en.wikipedia.org/wiki/False_position_method#The_regula_falsi_(false_position)_method)
      * `NewtonsMethodAD()`: 自動微分を使用した[ニュートン法](https://en.wikipedia.org/wiki/Newton%27s_method)
      * `NewtonsMethod()`: [ニュートン法](https://en.wikipedia.org/wiki/Newton%27s_method)
  * `soltype` は次のいずれかの解の型です：    `CompactSolution` GPU対応。解は`converged`と`root`のみを持ちます。詳細は[`CompactSolutionResults`](@ref)を参照してください。    `VerboseSolution` CPU専用。解は追加の診断情報を持ちます。詳細は[`VerboseSolutionResults`](@ref)を参照してください。
  * `tol` は反復を停止するタイミングを決定するための許容誤差の型です。
  * `maxiters` は最大反復回数です。
