```julia
makePointFromCoords(M, coords)
makePointFromCoords(M, coords, u0)
makePointFromCoords(M, coords, u0, ϵ)
makePointFromCoords(M, coords, u0, ϵ, retraction_method)

```

座標を希望するマンフォールド上の点に変換するためのヘルパー関数。

DevNotes

  * FIXME この関数の統合を大幅に改善するか、完全に削除する必要があります。

      * この関数は群に対してあまりにも強い仮定をしています。

Notes

  * `u0` は点のデータ型を識別するために使用されます。
  * 必要に応じて異なる `exp` を渡してください。
