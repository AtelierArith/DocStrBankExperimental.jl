```
ForceIntensity{T<:Number, F<:Function}
```

分散力（力の強度）タイプ。

力の強度クラス。物理単位は単位体積あたりの力であり、体積は力が適用される多様体によって異なります：

  * force/length^3（3次元固体に適用される場合）、
  * force/length^2（表面に適用される場合）、
  * force/length^1（曲線に沿って適用される場合）、または
  * force/length^0（点に適用される場合）。

任意の点 `XYZ` での力の値を計算するための関数のシグネチャ。要素のヤコビ行列の列、`tangents`、有限要素識別子、`feid` を使用します：

```
getforce!(forceout::Vector{CT}, XYZ::Matrix{T}, tangents::Matrix{T}, feid::IT) where {CT, T, IT}
```

[`DataCache`](@ref) がデータを保存するために使用されます。
