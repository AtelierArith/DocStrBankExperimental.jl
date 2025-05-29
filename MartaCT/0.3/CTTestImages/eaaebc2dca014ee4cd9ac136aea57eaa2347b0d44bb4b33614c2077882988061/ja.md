```
combine_images(imp::ImageParams{T}, rect::AbstractMatrix{T}, circle::AbstractMatrix{T}) where {T}
```

グレースケール画像を作成するためのヘルパー関数。

キャリブレーションのために、`rect`画像と`circle`画像を組み合わせます。円の画像はグレースケール画像よりも小さい必要があります！

関連情報: [`gray_scale_image`](@ref), [`circle_image`](@ref)
