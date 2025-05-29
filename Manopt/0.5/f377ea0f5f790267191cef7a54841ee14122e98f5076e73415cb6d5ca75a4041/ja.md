```
NonlinearLeastSquaresObjective{E<:AbstractEvaluationType} <: AbstractManifoldObjective{T}
```

非線形最小二乗問題をモデル化するための目的

$$
\operatorname*{arg\,min}_{p ∈ \mathcal M} \frac{1}{2} \sum_{i=1}^m \lvert f_i(p) \rvert^2
$$

ここで、$f: \mathcal M → ℝ^m$ は成分関数 $f_i: \mathcal M → ℝ$（$i=1,…,m$）で書かれ、各成分関数は連続的に微分可能です。

非線形最小二乗問題を指定します。

# フィールド

  * `objective`: コスト関数のベクトル $f_i$（またはコストのベクトルを返す関数）とその勾配 $\operatorname{grad} f_i$（またはベクトル値関数のヤコビ行列）を含む [`AbstractVectorGradientFunction`](@ref)`{E}`。

この `NonlinearLeastSquaresObjective` は、（内部）`objective` と同じ [`AbstractEvaluationType`](@ref) `T` を持ちます。

# コンストラクタ

```
NonlinearLeastSquaresObjective(f, jacobian, range_dimension::Integer; kwargs...)
NonlinearLeastSquaresObjective(vf::AbstractVectorGradientFunction)
```

# 引数

  * `f` ベクトルコスト関数 $f: \mathcal M → ℝ^m$
  * `jacobian` ヤコビ行列、`f` の成分関数の勾配のベクトルでもあるかもしれません
  * `range_dimension::Integer` 関数 `f` がマッピングする次元数 `m`

これら三つは、すでに [`AbstractVectorGradientFunction`](@ref) `vf` として渡すこともできます。

# キーワード引数

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることによって動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、修正された引数は二番目のものです。
  * `function_type::`[`AbstractVectorialType`](@ref)`=`[`FunctionVectorialType`](@ref)`()`: 残差が与えられる形式を指定します。デフォルトではベクトルを返す関数です。
  * `jacobian_tangent_basis::AbstractBasis=DefaultOrthonormalBasis()`; ヤコビ行列が構築される基底を指定するためのショートカット。
  * `jacobian_type::`[`AbstractVectorialType`](@ref)`=`[`CoordinateVectorialType`](@ref)`(jacobian_tangent_basis)`: ヤコビ行列が与えられる形式を指定します。デフォルトでは、接空間の特定の基底に関する微分の行列です。

# 参照

[`LevenbergMarquardt`](@ref), [`LevenbergMarquardtState`](@ref)
