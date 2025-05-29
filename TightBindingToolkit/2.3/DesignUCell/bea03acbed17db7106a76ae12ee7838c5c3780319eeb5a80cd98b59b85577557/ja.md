```julia
ModifyFields!(uc::UnitCell, site::Int64, newField::Vector{Float64})
ModifyFields!(uc::UnitCell, newField::Vector{Vector{Float64}})
```

`UnitCell`内のオンサイトフィールドを、1つずつまたはすべて一度に変更します。
