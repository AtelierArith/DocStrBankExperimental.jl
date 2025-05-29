```
StencilRecurrence{N,T,S,
    COEF<:NTuple{S,AbstractArray{T,N}},
    TB<:AbstractArray{T,N},}
    (stencil, coef, buffer, slicestart, sliceend, lastind)
```

# パラメータ

  * `N`: システム次元
  * `T`: エレメンタリタイプ
  * `S`: ステンシルサイズ

# プロパティ

`coef` と `slicesupport` については、パフォーマンスのために遅延配列を使用することをお勧めします。

  * `stencil::NTuple{S, CartesianIndex{N}}`: ステンシルの相対インデックス。 `(0,0)` を含むことができます（`coef` を参照）。
  * `coef::COEF<:NTuple{S,AbstractArray{T,N}}`: 各相対インデックスに関連付けられた係数。 `CartesianIndex(0,0)` に関連付けられたものは、そのエントリに追加される定数を指します。パフォーマンスのために遅延配列を使用することをお勧めします。
  * `buffer::CircularArray{T,N,TB<:AbstractArray{T,N}}`: 一時的な結果を保存するためのバッファ。
  * `slicestart::MVector{N, Int}` と `sliceend::MVector{N, Int}`: 現在のエントリの範囲を示します。技術的には `NTuple{N-1, Int}` が機能するはずですが、`Julia` は計算された型パラメータをサポートしていません。
  * `lastslice::Int`: 再帰が終了するスライスのインデックスを示します。
