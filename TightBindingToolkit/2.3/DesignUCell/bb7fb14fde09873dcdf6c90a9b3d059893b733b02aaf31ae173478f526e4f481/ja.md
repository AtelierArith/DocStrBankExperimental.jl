```julia
ModifyBonds!(uc::UnitCell, dist::Float64, newMat::Matrix{<:Number})
ModifyBonds!(uc::UnitCell, label::String, newMat::Matrix{<:Number})
```

与えられた `label` を持つ既存の結合を `UnitCell` 内で修正するか、指定された距離=`dist` で与えられた結合行列に修正します。
