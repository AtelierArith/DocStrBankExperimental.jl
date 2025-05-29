```
assemble!(self::SysvecAssembler{T}, vec::MV,
  dofnums::D) where {T<:Number, MV<:AbstractArray{T}, D<:AbstractArray{FInt}}
```

要素ごとのベクトルを組み立てます。

このメソッドは、行の自由度番号のベクトルを使用して列要素ベクトルを組み立てます。
