```
simulation(image::Array{T,3}, simParams::Dict) where T<:AbstractFloat
```

与えられた `image` データからMRI生データをシミュレートします。すべてのシミュレーションパラメータは辞書の形式で関数に渡されます。
