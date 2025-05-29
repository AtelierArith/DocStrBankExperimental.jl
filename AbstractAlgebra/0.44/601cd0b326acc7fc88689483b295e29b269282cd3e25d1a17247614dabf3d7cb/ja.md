```
intersect(M::FPModule{T}, N::FPModule{T}) where T <: RingElement
```

モジュール $M$ の部分モジュールとしての交差を返します。$M$ と $N$ は、共通のモジュール $P$ の部分モジュール（推移的に）である必要があることに注意してください。
