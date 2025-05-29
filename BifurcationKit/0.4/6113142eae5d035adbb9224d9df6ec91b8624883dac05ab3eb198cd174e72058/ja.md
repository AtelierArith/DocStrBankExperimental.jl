```julia
struct DeflationOperator{Tp<:Real, Tdot, T<:Real, vectype} <: BifurcationKit.AbstractDeflationFactor
```

カスタム距離を定義するための構造体。

このオペレーターは、次の状況を処理することを可能にします。ニュートンアルゴリズムを使用して `F(x)=0` を解決したいが、すでに知られている解 $roots_i$ を返さないようにしたいとします。デフレーションオペレーターはこれらの根にペナルティを課します。スカラー関数 `M(u)` を定義するために `DeflationOperator` を作成し、ニュートン反復を使用して次の関数のゼロを見つけるために使用します $F(u) \cdot Π_i(\|u - root_i\|^{-2p} + \alpha) := F(u) \cdot M(u)$ ここで $\|u\|^2 = dot(u, u)$ です。構造体 `DeflationOperator` のフィールドは次のとおりです：

  * `power::Real`: 指数 `p`。例えば `Int` を使用できます
  * `dot::Any`: 関数。この関数は線形ソルバーがうまく機能するために双線形かつ対称である必要があります
  * `α::Real`: シフト
  * `roots::Vector`: 根
  * `tmp::Any`
  * `autodiff::Bool`
  * `δ::Real`

`defOp::DeflationOperator` が与えられた場合、`defOp[n]` を使用してその根にアクセスできます。これは `defOp.roots[n]` のショートカットです。`defOp[end]` を使用することもできます。

また、`push!(defOp, newroot)` を使用して新しい根を追加（または `pop!(defOp)` で削除）することができます。最後に、`length(defOp)` は `length(defOp.roots)` のショートカットです。

## コンストラクタ

  * `DeflationOperator(p::Real, α::Real, roots::Vector{vectype}; autodiff = false)`
  * `DeflationOperator(p::Real, dt, α::Real, roots::Vector{vectype}; autodiff = false)`
  * `DeflationOperator(p::Real, α::Real, roots::Vector{vectype}, v::vectype; autodiff = false)`

オプション `autodiff` はスカラー関数 `M` の勾配の計算に自動微分を使用することをトリガーします。これは現在のところ `AbstractVector` のみで機能します。

## カスタム距離

`DeflationOperator` を構築するために `dot` のようなスカラー積を渡すように求められます。ただし、場合によってはカスタム距離 `dist(u, v)` を渡したいことがあります。これを使用して行うことができます。

```
`DeflationOperator(p, CustomDist(dist), α, roots)`
```

`CustomDist(dist, true)` を渡すと、`M` の勾配のために自動微分の使用がトリガーされることに注意してください。

## 線形ソルバー

ニュートンと一緒に使用されると、次の線形ソルバーにアクセスできます。

  * カスタムソルバー `DeflatedProblemCustomLS()` は、2つの線形システム `J⋅x = rhs` を解く必要があります。
  * 他の線形ソルバー `<: AbstractLinearSolver` については、デフレートされた関数のために行列フリーの方法が使用されます。
  * `Val(:autodiff)` が渡された場合、`ForwardDiff.jl` がデフレートされた問題のヤコビ行列を計算するために使用されます。
  * `Val(:fullIterative)` が渡された場合、デフレートされた問題のために完全な行列フリーの方法が使用されます。
