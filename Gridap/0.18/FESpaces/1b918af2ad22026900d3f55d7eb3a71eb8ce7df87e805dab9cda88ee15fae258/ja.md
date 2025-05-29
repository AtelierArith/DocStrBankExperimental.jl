```
struct ConstantFESpace <: SingleFieldFESpace
  # プライベートフィールド
end

ConstantFESpace(model::DiscreteModel; vector_type=Vector{Float64}, field_type=Float64)
ConstantFESpace(trian::Triangulation; vector_type=Vector{Float64}, field_type=Float64)
```

提供されたモデル/三角形分割に対して一定のFESpace。通常、ラグランジュ乗数として使用されます。キーワード引数 `vector_type` と `field_type` は、それぞれdofベクトルとdof値の型を指定するために使用されます。
