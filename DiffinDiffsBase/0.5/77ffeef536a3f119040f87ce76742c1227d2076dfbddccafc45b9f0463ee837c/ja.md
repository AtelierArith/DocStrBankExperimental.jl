```
NotYetTreatedParallel{C,S} <: TrendParallel{C,S}
```

比較的早く治療を受けたグループと比較的遅く（または決して）治療を受けなかったグループの間で平行トレンドの仮定が成り立つと仮定します。詳細は[`notyettreated`](@ref)を参照してください。

# フィールド

  * `e::Tuple{Vararg{ValidTimeType}}`: 比較的遅く治療を受けたユニットのグループインデックス。
  * `ecut::Tuple{Vararg{ValidTimeType}}`: `e`のグループ内のユニットが治療を受け始めた期間または期待効果を示した期間。
  * `c::C`: [`ParallelCondition`](@ref)のインスタンス。
  * `s::S`: [`ParallelStrength`](@ref)のインスタンス。

!!! note
    `ecut`は次のような場合に`minimum(e)`とは異なる可能性があります。

      * 治療を受けていないグループが含まれ、より小さい値のインデックスを使用している場合。
      * サンプルが他のいくつかの期間と重複する期間を持つ回転パネル構造を持っている場合。

