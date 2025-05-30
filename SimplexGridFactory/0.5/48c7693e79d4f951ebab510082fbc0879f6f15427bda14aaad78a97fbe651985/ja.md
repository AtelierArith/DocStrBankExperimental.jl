```
model3d!(builder, filename; translate=(0,0,0), cellregion=0, hole=false)
```

ファイルから3Dモデルをロードします。ファイル形式は[MeshIO.jl](https://github.com/JuliaIO/MeshIO.jl)でサポートされているものです。
