```
direct_sum(m::Vector{<:FPModule{T}}) where T <: RingElement
direct_sum(vals::FPModule{T}...) where T <: RingElement
```

タプル $M, f, g$ を返します。ここで、$M$ はモジュール `m` の直和（モジュールのベクトルとして供給される）、$f$ は $m[i]$ を $M$ に注入するベクトル、$g$ は $M$ から $m[i]$ への射影のベクトルです。
