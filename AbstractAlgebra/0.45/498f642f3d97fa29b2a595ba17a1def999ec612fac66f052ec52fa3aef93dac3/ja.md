```
identity_matrix(M::MatElem{T}) where T <: NCRingElement
```

同じ行列空間における単位行列を構築します。すなわち、対角線上に1があり、それ以外は0です。`M`は正方行列でなければなりません。これは`one(M)`のエイリアスです。
