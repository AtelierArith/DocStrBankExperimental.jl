```
NonlinearLeastSquaresObjective{T<:AbstractEvaluationType} <: AbstractManifoldObjective{T}
```

非線形最小二乗問題のための型です。`T`は`F`およびヤコビ行列関数のための[`AbstractEvaluationType`](@ref)です。

非線形最小二乗問題を指定します

# フィールド

  * `f`                      最小化する関数 $f: \mathcal M → ℝ^d$
  * `jacobian!!`             関数 $f$ のヤコビ行列
  * `jacobian_tangent_basis` ヤコビ行列を計算するために使用される接空間の基底。
  * `num_components`         `f` によって返される値の数（`d` に等しい）。

[`AbstractEvaluationType`](@ref) `T` に応じて、関数 $F$ を提供する必要があります：

  * メモリを自分自身で確保する関数 `(M::AbstractManifold, p) -> v` として、[`AllocatingEvaluation`](@ref) のために、
  * `v` のインプレースで動作する関数 `(M::AbstractManifold, v, p) -> v` として、[`InplaceEvaluation`](@ref) のために。

また、ヤコビ行列 $jacF!!$ も必要です：

  * メモリを自分自身で確保する関数 `(M::AbstractManifold, p; basis_domain::AbstractBasis) -> v` として、[`AllocatingEvaluation`](@ref) のために、
  * `v` のインプレースで動作する関数 `(M::AbstractManifold, v, p; basis_domain::AbstractBasis) -> v` として、[`InplaceEvaluation`](@ref) のために。

# コンストラクタ

```
NonlinearLeastSquaresProblem(M, F, jacF, num_components; evaluation=AllocatingEvaluation(), jacobian_tangent_basis=DefaultOrthonormalBasis())
```

# 参照

[`LevenbergMarquardt`](@ref), [`LevenbergMarquardtState`](@ref)
