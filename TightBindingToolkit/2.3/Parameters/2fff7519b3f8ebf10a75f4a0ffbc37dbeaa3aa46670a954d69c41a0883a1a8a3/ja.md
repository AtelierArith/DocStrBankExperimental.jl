```julia
AddAnisotropicBond!( param::Param, uc::UnitCell , base::Int64 , target::Int64 , offset::Vector{Int64} , mat::Number , dist::Float64, label::String )
AddAnisotropicBond!( param::Param, uc::UnitCell , base::Int64 , target::Int64 , offset::Vector{Int64} , mat::Matrix{<:Number} , dist::Float64, label::String )
```

与えられた属性を持つ結合を `param` に追加します。与えられた `mat` 属性が数値である場合、結合に入るときに 1x1 行列に変換されます。
