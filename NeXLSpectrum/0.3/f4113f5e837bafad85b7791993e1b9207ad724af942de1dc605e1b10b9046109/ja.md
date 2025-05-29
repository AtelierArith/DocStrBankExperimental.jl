```
annotate(
    img::AxisArray; 
    scale::Bool = true,
    coords::Union{Nothing, AbstractArray{<:AbstractDict{Symbol, <:AbstractFloat}}} = nothing,
    spectra::Union{Nothing, <:AbstractArray{<:Spectrum}} = nothing,
    thumbnails::Union{Nothing, AbstractArray{<:AxisArray}}=nothing,
    labelcoords::Bool = true,
    labelthumbnails::Bool = true,
    marker::Colorant = HSVA(60, 1, 1, 0.3) 
)
```

画像にスケールバー、取得ポイント、画像領域などの注釈を追加し、結果を表示します。

  * `coords` と `spectra` は円（数値ラベルの有無にかかわらず）として表示されます。
  * `thumbnails` は画像に重ねて表示される矩形として表示されます。
  * `scale` は右上隅にスケールバーとして表示されます。
  * `marker` は注釈の色で、デフォルトではわずかに透明です。
