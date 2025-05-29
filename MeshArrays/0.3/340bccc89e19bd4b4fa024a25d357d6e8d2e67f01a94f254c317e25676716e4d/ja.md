```
gcmgrid
```

gcmgrid データ構造。利用可能なコンストラクタ：

```
gcmgrid(path::String, class::String, nFaces::Int, 
        fSize::Array{NTuple{2, Int},1},
        ioSize::Union{NTuple{2, Int},Array{Int64,2}},
        ioPrec::Type, read::Function, write::Function)
```

`class` は "LatLonCap", "CubeSphere", "PeriodicChannel", "PeriodicDomain" に設定できます。

例えば、サイズ 360 x 160 の周期的チャネル（x方向に周期的）は、次のように定義できます。

```
pth=MeshArrays.GRID_LL360
class="PeriodicChannel"
ioSize=(360, 160)
ioPrec=Float32

γ=gcmgrid(pth, class, 1, [ioSize], ioSize, ioPrec, read, write)

Γ=GridLoad(γ)    
```

`gcmgrid` オプションに関連する詳細については、`GridSpec` と `UnitGrid` を参照してください。
