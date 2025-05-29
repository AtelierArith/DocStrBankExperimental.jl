```
struct FusionTree{I, N, M, L}
```

型 `I<:Sector` のセクターの融合木を表します。これは `N` の非結合セクターを結合されたセクターに融合（または分割）します。実際には分割木を表しますが、融合木という用語の方が一般的です。

## フィールド

  * `uncoupled::NTuple{N,I}`: 分割木から出てくる非結合セクターで、可能な 𝑍 同型（`isdual` を参照）前のものです。
  * `coupled::I`: 結合されたセクター。
  * `isdual::NTuple{N,Bool}`: 各非結合セクターに対して 𝑍 同型が存在するかどうかを示します（`true`）または存在しない（`false`）。
  * `innerlines::NTuple{M,I}`: 分割木の `M=max(0, N-2)` の内線のラベル。
  * `vertices::NTuple{L,Int}`: 分割木の `L=max(0, N-1)` の頂点の整数値。もし `FusionStyle(I) isa MultiplicityFreeFusion` であれば、`vertices` は単に定数値 `ntuple(n->1, L)` に等しくなります。
