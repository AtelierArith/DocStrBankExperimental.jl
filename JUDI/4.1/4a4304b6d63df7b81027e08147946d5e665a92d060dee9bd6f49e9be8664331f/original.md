```
GeometryIC
    xloc::Array{Array{T, 1},1}
    yloc::Array{Array{T, 1},1}
    zloc::Array{Array{T, 1},1}
    t::Vector{StepRangeLen{T}}
```

Geometry structure for seismic sources or receivers. Each field is a cell array, where individual cell entries contain values or arrays with coordinates and sampling information for the corresponding shot position. The  first three entries are in meters and the last three entries in milliseconds.

```
GeometryOOC{T} <: Geometry{T}
    container::Array{SegyIO.SeisCon,1}
    t::Vector{StepRangeLen{T}}
    nrec::Array{Integer,1}
    key::String
    segy_depth_key::String
```

# Constructors

Only pass `dt` and `n` and automatically set `t`:

```
Geometry(xloc, yloc, zloc; dt=[], nt=[])
```

Pass single array as coordinates/parameters for all `nsrc` experiments:

```
Geometry(xloc, yloc, zloc, dt=[], nt=[], nsrc=1)
```

Create geometry structure for either source or receivers from a SegyIO.SeisBlock object. `segy_depth_key` is the SegyIO keyword that contains the depth coordinate and `key` is  set to either `source` for source geometry or `receiver` for receiver geometry:

```
Geometry(SeisBlock; key="source", segy_depth_key="")
```

Create geometry structure for from a SegyIO.SeisCon object (seismic data container):

```
Geometry(SeisCon; key="source", segy_depth_key="")
```

# Examples

(1) Set up receiver geometry for 2D experiment with 4 source locations and 80 fixed receivers:

```
xrec = range(100,stop=900,length=80)
yrec = range(0,stop=0,length=80)
zrec = range(50,stop=50,length=80)
dt = 4f0
t = 1000f0

rec_geometry = Geometry(xrec, yrec, zrec; dt=dt, t=t, nsrc=4)
```

(2) Set up corresponding source geometry (coordinates can be of type `linspace` or regular arrays):

```
xsrc = [200,400,600,800]
ysrc = [0,0,0,0]
zsrc = [50,50,50,50]

src_geometry = Geometry(xsrc, ysrc, zsrc; dt=dt, t=t, nsrc=4)
```

(3) Read source and receiver geometries from SEG-Y file:

```
using SegyIO
seis_block = segy_read("test_file.segy")
rec_geometry = Geometry(seis_block; key="receiver", segy_depth_key="RecGroupElevation")
src_geometry = Geometry(seis_block; key="source", segy_depth_key="SourceDepth")
```

Check the seis_block's header entries to findall out which keywords contain the depth coordinates. The source depth keyword is either `SourceDepth` or `SourceSurfaceElevation`. The receiver depth  keyword is typically `RecGroupElevation`.

(4) Read source and receiver geometries from out-of-core SEG-Y files (for large data sets). Returns an out-of-core  geometry object `GeometryOOC` without the source/receiver coordinates, but a lookup table instead:

```
using SegyIO
seis_container = segy_scan("/path/to/data/directory","filenames",["GroupX","GroupY","RecGroupElevation","SourceDepth","dt"])
rec_geometry = Geometry(seis_container; key="receiver", segy_depth_key="RecGroupElevation")
src_geometry = Geometry(seis_container; key="source", segy_depth_key="SourceDepth")
```
