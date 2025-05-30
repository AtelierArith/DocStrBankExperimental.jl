```
model3d!(builder, filename; translate=(0,0,0), cellregion=0, hole=false)
```

ファイルから3Dモデルを読み込みます。ファイル形式は[MeshIO.jl](https://github.com/JuliaIO/MeshIO.jl)でサポートされているものです。
