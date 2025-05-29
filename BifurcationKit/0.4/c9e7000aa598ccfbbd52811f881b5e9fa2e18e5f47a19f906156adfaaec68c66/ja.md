```julia
struct EigArnoldiMethod{T, Tby, Tw, Tkw, vectype} <: BifurcationKit.AbstractIterativeEigenSolver
```

## フィールド

  * `sigma::Any`: シフトインバート法のためのシフト
  * `which::Any`: 抽出する固有要素 LR(), LM(), ...
  * `by::Any`: 計算された固有値をどのようにソートするか、デフォルトは実数
  * `kwargs::Any`: EigArpack に渡されるキーワード引数
  * `x₀::Any`: Krylov 反復に使用されるベクトルの例

詳細情報は [ArnoldiMethod.jl](https://github.com/haampie/ArnoldiMethod.jl) で入手できます。たとえば、`tol, mindim, maxdim, restarts` のパラメータを渡すことができます。

# コンストラクタ

`EigArnoldiMethod(;sigma = nothing, which = ArnoldiMethod.LR(), x₀ = nothing, kwargs...)`
