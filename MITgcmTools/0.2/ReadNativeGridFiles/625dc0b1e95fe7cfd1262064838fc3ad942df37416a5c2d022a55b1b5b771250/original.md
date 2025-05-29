```
GridLoad_native(path,files,γ)
```

Load grid variables from native grid files.

```
path="GRID_LLC90"
files=["tile001.mitgrid","tile002.mitgrid","tile003.mitgrid","tile004.mitgrid","tile005.mitgrid"]
ioSize=[90 1170]
facesSize=[(90, 270), (90, 270), (90, 90), (270, 90), (270, 90)]

γ=gcmgrid(path,"LatLonCap",5,facesSize, ioSize, Float64, read, write)

Γ=GridLoad_native(path,files,γ)
```

or using another grid

```
path="llc_1080"
files=[ "llc_001_1080_3240.bin","llc_002_1080_3240.bin",
        "llc_003_1080_1080.bin","llc_004_3240_1080.bin","llc_005_3240_1080.bin"]
ioSize=[1080 14040]
facesSize=[(1080, 3240), (1080, 3240), (1080, 1080), (3240, 1080), (3240, 1080)]
```

and for plotting 

```
using GLMakie

#col=log10.(Γ.RAC); rng=(4,8)

#using MAT
#Depth=get_bathy(path,γ)
#col=write(Depth); rng=(-5000,5000)

XC=write(Γ.XC); YC=write(Γ.YC)
ii=findall((XC.>-80).&(XC.<-10).&(YC.>-10).&(YC.<60))
#ii=findall((XC.>-80).&(XC.<-60).&(YC.>15).&(YC.<35))

#ii=1:prod(γ.ioSize)

scatter(XC[ii],YC[ii],color=col[ii],colorrange=rng,markersize=0.1, markerspace = :data)
```
