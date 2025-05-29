```
savenii(image::AbstractArray, filepath; header=nothing, kwargs...)

savenii(image::AbstractArray, name, writedir, header=nothing, kwargs...)
```

警告: MRIcroはInt32、Int64、Float32、Float64のタイプの画像のみを開くことができます。

# 例

```julia-repl
julia> savenii(ones(64,64,5), "image.nii")

julia> savenii(ones(64,64,5), "image2", "folder")

julia> savenii(ones(64,64,5), "image2", "folder"; voxel_size=(0.54,0.54,2.0))
```
