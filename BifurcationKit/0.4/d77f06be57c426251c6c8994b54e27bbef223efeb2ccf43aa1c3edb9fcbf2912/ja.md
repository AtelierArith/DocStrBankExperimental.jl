```julia
struct EigArpack{T, Tby, Tw} <: BifurcationKit.AbstractIterativeEigenSolver
```

[Arpack.jl](https://github.com/JuliaLinearAlgebra/Arpack.jl)に基づく固有値ソルバーを作成します。

## フィールド

  * `sigma::Any`: シフトインバート法のためのシフト `(J - sigma⋅I)`
  * `which::Symbol`: 抽出する固有要素 :LR, :LM, ...
  * `by::Any`: ソート関数、デフォルトは実数
  * `kwargs::Any`: EigArpackに渡されるキーワード引数

# コンストラクタ

`EigArpack(sigma = nothing, which = :LR; kwargs...)`

詳細情報は[Arpack.jl](https://github.com/JuliaLinearAlgebra/Arpack.jl)で入手できます。次のパラメータを渡すことができます `tol = 0.0, maxiter = 300, ritzvec = true, v0 = zeros((0,))`。
