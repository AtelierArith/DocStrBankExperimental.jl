```julia
struct SectionPS{Tn, Tc, Tnb, Tcb, Tr} <: BifurcationKit.AbstractSection
```

この複合型（SectionPoincaréShootingの名前が付けられています）は、ハイパープレーンによって実装されたポアンカレセクションの一種をエンコードします。これは[`PoincareShootingProblem`](@ref)と組み合わせて使用できます。各ハイパープレーンは、点（`centers`の一例）と法線（`normals`の一例）によって定義されます。

  * `M::Int64`
  * `normals::Any`
  * `centers::Any`
  * `indices::Vector{Int64}`
  * `normals_bar::Any`
  * `centers_bar::Any`
  * `radius::Any`

# コンストラクタ

```
SectionPS(normals, centers)
```
