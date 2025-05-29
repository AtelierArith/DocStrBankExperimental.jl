```
InfiniteWeightPEPS([f=randn, T=ComplexF64,] Pspaces::M, Nspaces::M, [Espaces::M]) where {M<:AbstractMatrix{<:Union{Int,ElementarySpace}}}
```

単位セル内の各サイトにおけるPEPS頂点テンソルの物理、北の仮想および東の仮想空間を行列として指定することにより、InfiniteWeightPEPSを作成します。各個別の空間は、`Int`または`ElementarySpace`のいずれかとして指定できます。ボンドの重みは、要素型`Float64`の単位行列として初期化されます。
