```julia
struct PeriodicOrbitOCollProblem{Tprob<:Union{Nothing, BifurcationKit.AbstractBifurcationProblem}, Tjac<:BifurcationKit.AbstractJacobianType, 𝒯, vectype, ∂vectype, Tmass} <: BifurcationKit.AbstractPODiffProblem
```

この複合型は、周期軌道を特定するために区分的多項式のガウスポイントでの直交コレクション法を実装しています。詳細（数学、表記、線形システム）は[こちら](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/periodicOrbitCollocation/)で確認できます。

## フィールド

  * `prob_vf::Union{Nothing, BifurcationKit.AbstractBifurcationProblem}`: `prob`は分岐問題です。デフォルト: nothing
  * `ϕ::Any`: 位相制約方程式のセクションを設定するために使用されます。デフォルト: nothing
  * `xπ::Any`: 位相制約方程式のセクションで使用されます。デフォルト: nothing
  * `∂ϕ::Any`: ϕの導関数を保存します。毎回再計算する必要はありません。デフォルト: nothing
  * `N::Int64`: 状態空間の次元。デフォルト: 0
  * `isautonomous::Bool`: デフォルト: true
  * `massmatrix::Any`: デフォルト: nothing
  * `update_section_every_step::UInt64`: 継続中に`update_section_every_step`ステップごとにセクションを更新します。デフォルト: 1
  * `jacobian::BifurcationKit.AbstractJacobianType`: ニュートン反復で使用されるヤコビアンのタイプを説明します。`AutoDiffDense(), DenseAnalytical(), FullSparse(), FullSparseInplace(), DenseAnalyticalInplace()`のいずれかでなければなりません。デフォルト: DenseAnalytical()
  * `mesh_cache::BifurcationKit.MeshCollocationCache`: コレクションのためのキャッシュです。`MeshCollocationCache`のドキュメントを参照してください。デフォルト: nothing
  * `cache::BifurcationKit.POCollCache`: デフォルト: nothing
  * `meshadapt::Bool`: メッシュ適応を使用するかどうか。デフォルト: false
  * `verbose_mesh_adapt::Bool`: デフォルト: false
  * `K::Float64`: メッシュ適応のためのパラメータで、新しいメッシュのステップサイズを制御します。より正確には、hᵢが時間ステップを示す場合、max(hᵢ) / min(hᵢ) ≤ Kを設定します。デフォルト: 100

## メソッド

`pb`に適用できるいくつかの便利なメソッドは次のとおりです。

  * `length(pb)`は未知数の総数を返します。
  * `size(pb)`は三重項`(N, m, Ntst)`を返します。
  * `getmesh(pb)`はメッシュ`0 = τ₀ < ... < τₙₜₛₜ₊₁ = 1`を返します。これは、自動メッシュ適応中に変化するため、便利です。
  * `get_mesh_coll(pb)`は（静的な）メッシュ`0 = σ₀ < ... < σₘ₊₁ = 1`を返します。
  * `get_times(pb)`はコレクションが適用される時間のベクトル（長さ`1 + m * Ntst`）を返します。
  * `generate_solution(pb, orbit, period)`は周期軌道を近似する関数`t -> orbit(t)`から推測を生成します。
  * `POSolution(pb, x)`は区分的多項式関数を使用して解`x`を補間する関数を返します。

# 軌道の推測

`pb(orbitguess, p)`を呼び出すことで、機能の残差（および他のもの）を評価できます。`orbitguess`はサイズが1 + N * (1 + m * Ntst)でなければならず、ここでNは状態空間の未知数の数であり、`orbitguess[end]`はリミットサイクルの周期$T$の推定値です。

この推測は、`generate_solution`または`generate_ci_problem`を使用して関数から生成できます。

# コンストラクタ

  * `PeriodicOrbitOCollProblem(Ntst::Int, m::Int; kwargs)`は`Ntst`と`m`を持つ空の機能を作成します。

# 機能

機能は、ここで`G`と呼ばれ、この問題をエンコードします。以下のメソッドが利用可能です。

  * `residual(pb, orbitguess, p)`は`orbitguess`上で機能Gを評価します。
  * `residual!(pb, out, orbitguess, p)`は`orbitguess`上で機能Gを評価します。

```
