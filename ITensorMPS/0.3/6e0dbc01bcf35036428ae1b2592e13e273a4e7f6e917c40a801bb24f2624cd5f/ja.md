```
promote_itensor_eltype(m::MPS)
promote_itensor_eltype(m::MPO)
```

MPSまたはMPO内のテンソルの要素タイプの昇格を返します。たとえば、すべてのテンソルが`Float64`型であれば、`Float64`を返します。しかし、1つ以上のテンソルが`ComplexF64`型であれば、`ComplexF64`を返します。
