```julia
struct SectionSS{Tn} <: BifurcationKit.AbstractSection
```

この複合型（セクション標準射撃のために名付けられた）は、単一のハイパープレーンによって実装されたセクションの一種をエンコードします。これは[`ShootingProblem`](@ref)と組み合わせて使用できます。ハイパープレーンは、点`center`と`normal`によって定義されます。

  * `normal::Any`: ハイパープレーンを定義する法線
  * `center::Any`: ハイパープレーン上の代表点
