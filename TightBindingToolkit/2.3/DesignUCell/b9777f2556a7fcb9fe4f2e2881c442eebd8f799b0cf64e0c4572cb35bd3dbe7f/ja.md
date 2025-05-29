```julia
ModifyIsotropicFields!(uc::UnitCell, newField::Vector{Float64})
ModifyIsotropicFields!(uc::UnitCell, newField::Float64, dim::Int64)
```

すべてのサブ格子で一様にオンサイトフィールドを修正します。オプションの引数 `dim` は、オンサイトフィールドの4つの要素のうちの1つ（3つのゼーマンと1つの化学ポテンシャル）だけを修正したい場合に使用します。
