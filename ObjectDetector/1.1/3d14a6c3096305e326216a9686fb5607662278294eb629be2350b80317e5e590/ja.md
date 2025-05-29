```
prepare_image(img::AbstractArray{T}, model::U) where {T<:ImageCore.Colorant, U<:AbstractModel}
prepare_image(img::AbstractArray{T}, img_resized_size::Tuple, kern) where {T<:ImageCore.Colorant}
prepare_image!(dest_arr::AbstractArray{Float32}, img::AbstractArray{T}, kern) where {T<:Real}
prepare_image!(dest_arr::AbstractArray{Float32}, img::AbstractArray{T}, kern) where {T<:ImageCore.Colorant}
```

指定された形状に収まるように画像を読み込み、準備（リサイズ + パディング）します。入力画像は列優先（juliaのデフォルト）である必要があり、行優先（darknet）に変換されます。
