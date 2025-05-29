```julia
AddIsotropicBonds!( uc::UnitCell{T} , dist::Float64 , mats::Number , label::String; checkOffsetRange::Int64=1 , subs::Vector{Int64}=collect(1:length(uc.basis)))
AddIsotropicBonds!( uc::UnitCell{T} , dist::Float64 , mats::Array{<:Number, T} , label::String; checkOffsetRange::Int64=1 , subs::Vector{Int64}=collect(1:length(uc.basis)) )
```

与えられた距離で各サイトのペアに対して同じである「等方的」結合のセットを追加します。与えられた `mat` 属性が数値である場合、結合に入るときに1x1行列に変換されます。入力 `checkOffsetRange` は、入力距離に応じて調整する必要があります。オプションの入力 `subs` は、サブ格子のサブセットのみが関与する場合の等方的結合のために意図されています。
