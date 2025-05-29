```
simulation(image::Array{T,3}, simParams::Dict, filename::String) where T<:Union{Complex{<:AbstractFloat},AbstractFloat}
```

`simulation(image, simParams)`と同じシミュレーションを実行し、結果を`filename`という名前のファイルに保存します。
