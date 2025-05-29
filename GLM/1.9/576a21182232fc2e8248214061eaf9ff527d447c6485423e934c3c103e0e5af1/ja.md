```
negbin(formula, data, [link::Link];
       <keyword arguments>)
negbin(X::AbstractMatrix, y::AbstractVector, [link::Link];
       <keyword arguments>)
```

データに対して負の二項一般化線形モデルを適合させ、同時に形状パラメータ θ を推定します。追加の引数およびキーワード引数は [`glm`](@ref) に渡されます。

最初のメソッドでは、`formula` は [StatsModels.jl `Formula` オブジェクト](https://juliastats.org/StatsModels.jl/stable/formula/) でなければならず、`data` はテーブル（[Tables.jl](https://tables.juliadata.org/stable/) 定義、例えばデータフレーム）でなければなりません。2 番目のメソッドでは、`X` は独立変数の値を列に持つ行列でなければならず（必要に応じて切片を含む）、`y` は従属変数の値を持つベクトルでなければなりません。いずれの場合も、`link` はリンク関数を指定することができ（省略された場合は `NegativeBinomial(θ)` と見なされます）。

# キーワード引数

  * `initialθ::Real=Inf`: 形状パラメータ θ の開始値。`Inf` の場合、初期値はポアソン分布を適合させることによって推定されます。
  * `maxiter::Integer=30`: [`glm`](@ref) の `maxiter` を参照してください
  * `atol::Real=1.0e-6`: [`glm`](@ref) の `atol` を参照してください
  * `rtol::Real=1.0e-6`: [`glm`](@ref) の `rtol` を参照してください
  * `verbose::Bool=false`: [`glm`](@ref) の `verbose` を参照してください
