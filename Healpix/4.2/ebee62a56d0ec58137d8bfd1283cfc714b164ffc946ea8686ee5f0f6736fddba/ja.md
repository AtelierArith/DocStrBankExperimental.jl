dot(alm₁::Alm{Complex{T}}, alm₂::Alm{Complex{T}}) where {T <: Number}

```
a_ℓm空間における内積を実装します。
2つの入力almは、サイズ、lmax、およびmmaxが一致している必要があります。
新しい`Alm`オブジェクトが返されます。
```
