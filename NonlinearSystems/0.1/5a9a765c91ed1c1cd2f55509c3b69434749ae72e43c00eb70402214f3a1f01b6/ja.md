```
NonlinearSystem(::Type{P}, fdf::OnceDifferentiable, x, fx, dx, solver; kwargs...)
```

非線形方程系を解くために使用されるすべての情報を保持する`NonlinearSystem`を構築します。問題のタイプ`P`に対して、ユーザーはこのメソッドを直接使用することは期待されておらず、代わりに`init`または`solve`を呼び出して問題を生成するべきです。`init`または`solve`に渡されるキーワード引数のうち、特定の解法アルゴリズムによって受け入れられないものは、`NonlinearSystem`のコンストラクタに渡されます。関連する解法アルゴリズムについては、[`Hybrid`](@ref)を参照してください。

# キーワード

  * `lower::Union{AbstractVector, Nothing}=nothing`: 解候補の要素ごとの下限。
  * `upper::Union{AbstractVector, Nothing}=nothing`: 解候補の要素ごとの上限。
  * `maxiter::Integer=1000`: 終了する前に許可される最大反復回数。
  * `ftol::Real=1e-8`: 残差`fx`の無限ノルムに対する絶対許容誤差。
  * `gtol::Real=1e-10`: 勾配ベクトルの無限ノルムに対する絶対許容誤差；最小二乗法を解く際にのみ関連。
  * `xtol::Real=0.0`: ステップ`dx`の無限ノルムに対する絶対許容誤差。
  * `xtolr::Real=0.0`: ステップ`dx`の無限ノルムに対する相対許容誤差；`x`の割合として。
  * `showtrace::Union{Bool,Integer}=false`: ソルバーによって行われた各試行の要約情報を印刷；`showtrace=true`の場合、情報は20回ごとに1回印刷される；整数値は印刷の間隔を指定します。

```
