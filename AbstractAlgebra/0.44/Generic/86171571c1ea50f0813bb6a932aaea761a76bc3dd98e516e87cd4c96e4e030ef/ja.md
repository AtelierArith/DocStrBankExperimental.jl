```
is_compatible(M::AbstractAlgebra.FPModule{T}, N::AbstractAlgebra.FPModule{T}) where T <: RingElement
```

与えられたモジュールが互換性がある場合は `true, P` を返します。すなわち、それらが同じモジュール P の（推移的な）部分モジュールであることを意味します。そうでない場合は `false, M` を返します。
