```
sub(m::FPModule{T}, gens::Vector{<:FPModuleElem{T}}) where T <: RingElement
```

モジュール `m` の部分モジュールを、与えられた生成子として `m` の要素で生成されたものを返します。
