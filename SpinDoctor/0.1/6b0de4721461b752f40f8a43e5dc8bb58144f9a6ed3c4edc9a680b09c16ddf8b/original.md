```
VTKWriter(; nupdate = 1, dir = "output", filename = "solution")
```

Write magnetization field to a VTK file after every `nupdate` timestep. The files are stored in a ParaView data collection file (PVD). The magnetization time series may be visualized in ParaView by opening the file `"$dir/$filename.pvd"`. The compartments are labeled.
