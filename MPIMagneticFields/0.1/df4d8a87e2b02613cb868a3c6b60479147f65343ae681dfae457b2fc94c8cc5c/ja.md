```julia
struct SuperimposedField{T<:MPIMagneticFields.AbstractMagneticField, U<:MPIMagneticFields.AbstractMagneticField} <: MPIMagneticFields.AbstractSuperimposedField
```

重ね合わせた場のコンテナ。

`fieldA` と `fieldB` の場は線形に重ね合わせられていると解釈されます。
