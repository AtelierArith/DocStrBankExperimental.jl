```
UInt12Array{T, B, N}(data::B [, size::NTuple{N,Int} ])
UInt12Array{T, B, N}(undef    , size::NTuple{N,Int}  )
```

UInt12Arrayは、密に詰められた12ビット整数の配列を表します。

UInt12AArrayは次のパラメータを持ちます: `T` - UInt12Arrayの要素型。通常、これはUInt12またはUInt16のいずれかです。デフォルトはUInt12Arrays.default_eltypeです。 `B` - UInt12Arrayの内部ベクターストレージのベース型。 `N` - 配列の次元数。
