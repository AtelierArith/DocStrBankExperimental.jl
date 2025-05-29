```
InfiniteWeightPEPS([f=randn, T=ComplexF64,] Pspace::S, Nspace::S, Espace::S=Nspace; unitcell::Tuple{Int,Int}=(1, 1)) where {S<:ElementarySpace}
```

物理、北、東の空間（`ElementarySpace`として）と単位セルサイズを指定してInfiniteWeightPEPSを作成します。`T`を使用して頂点テンソルの要素タイプを指定します。ボンド重みは要素タイプ`Float64`の単位行列として初期化されます。
