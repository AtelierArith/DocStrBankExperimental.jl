```
read_nctiles(fileName,fldName,mygrid; I, eccoVersion4Release4=false, verbose=false)
```

Read model output from NCTiles file and convert to MeshArray instance. Setting the keyword argument `eccoVersion4Release4=true` allows `read_nctiles` to read in ECCOv4r4 data which has a different file naming convention to previous versions.

```
mygrid=GridSpec("LatLonCap")
fileName="nctiles_grid/GRID"
Depth=read_nctiles(fileName,"Depth",mygrid)
hFacC=read_nctiles(fileName,"hFacC",mygrid)
hFacC=read_nctiles(fileName,"hFacC",mygrid,I=(:,:,1))
```
