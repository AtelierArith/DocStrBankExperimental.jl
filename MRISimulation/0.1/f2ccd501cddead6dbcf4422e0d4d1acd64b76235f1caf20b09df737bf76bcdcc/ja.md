```
simulation(image::Array{T,2}, simParams::Dict) where T<:Union{Complex{<:AbstractFloat},AbstractFloat}
```

与えられた `image` データからMRI生データをシミュレートします。すべてのシミュレーションパラメータは、辞書の形式で関数に渡されます。
