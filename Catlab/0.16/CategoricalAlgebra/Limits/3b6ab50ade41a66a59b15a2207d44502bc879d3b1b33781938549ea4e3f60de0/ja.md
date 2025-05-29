ダイアグラムの限界。

オブジェクト `Ob` を持つカテゴリで限界を定義するには、一般的な限界のために `limit(::FreeDiagram{Ob})` メソッドをオーバーライドするか、特定の形状の限界（例えば、積や同値器）については適切な型 `D <: FixedShapeFreeDiagram{Ob}` を用いて `limit(::D)` をオーバーライドします。

関連情報: [`colimit`](@ref)
