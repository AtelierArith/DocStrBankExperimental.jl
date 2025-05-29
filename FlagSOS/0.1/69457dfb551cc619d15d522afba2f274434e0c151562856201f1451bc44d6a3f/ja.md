```
HarmonicFlag{T} <: Flag where {T <: Flag}
```

与えられた Flag をその調和的な同等物に変換します。例えば、`HarmonicFlag{Graph}(P2)` の場合、ここで `P2 = Graph(Bool[0 0 1; 0 0 1; 1 1 0])` は三つの頂点のパスを表し、調和パス密度に対応する Flag を説明します。Flag 型 `T` に「エッジ」に相当するものがある場合にのみ意味があります。
