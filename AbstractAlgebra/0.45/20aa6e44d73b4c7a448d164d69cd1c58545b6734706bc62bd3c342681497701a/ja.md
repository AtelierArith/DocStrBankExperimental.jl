```
sub(m::FPModule{T}, gens::Vector{<:FPModuleElem{T}}) where T <: RingElement
```

与えられた生成子によって生成されたモジュール `m` の部分モジュールを返します。生成子は `m` の要素として与えられます。
