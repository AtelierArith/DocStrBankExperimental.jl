```
sub(m::Module{T}, subs::Vector{<:Generic.Submodule{T}}) where T <: RingElement
```

与えられた $m$ の部分モジュールの合併によって生成されるモジュール `m` の部分モジュール `S` と、`S` から `m` への標準的な注入である写像を返します。
