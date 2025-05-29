```julia
struct PALC{Ttang<:BifurcationKit.AbstractTangentComputation, Tbls<:BifurcationKit.AbstractLinearSolver, T, Tdot} <: BifurcationKit.AbstractContinuationAlgorithm
```

擬似アーク長連続体アルゴリズム。

追加情報は[ウェブサイト](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/PALC/)で入手できます。

# フィールド

  * `tangent::BifurcationKit.AbstractTangentComputation`: 接線予測器で、`AbstractTangentComputation`のサブタイプである必要があります。例えば`Secant()`や`Bordered()`。デフォルト: Secant()
  * `θ::Any`: `θ`はアーク長制約のパラメータです。調整することが非常に**重要**です。特に大規模な問題の場合、制約方程式の<x - x*0, dx*0>成分が過度に優遇される可能性があるため、連続体が適切に機能するように調整する必要があります。また、大きなθはpを優遇します。Nにおける対応する項は1-θを含むためです。デフォルト: 0.5
  * `_bothside::Bool`: [内部]、デフォルト: false
  * `bls::BifurcationKit.AbstractLinearSolver`: ニュートン反復中に境界付き問題のヤコビアンを反転するために使用される境界付き線形ソルバー。予測器`Bordered()`の接線を計算するためにも使用されます。デフォルト: MatrixBLS()
  * `dotθ::Any`: `dotθ = DotTheta()`、これは重み付き内積を定義するために使用される内積`(x, y) -> dot(x, y) / length(x)`を設定します。制約$N(x, p)$における重み付き内積（およびノルム）$\|(x, p)\|^2_\theta$を定義します（[PALC](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/PALC/)のオンラインドキュメントを参照）。この引数は、状態空間の次元が変化する問題（メッシュ適応など）や特定の（FEM）内積が提供される場合に、例えば`1/length(x)`の因子を削除するために使用できます。デフォルト: DotTheta()

```
