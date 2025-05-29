```
add_demag(sim::MicroSim; name="demag", Nx=0, Ny=0, Nz=0, fft=true)
```

Add Demag to the system. `Nx`, `Ny` and `Nz` can be used to describe the macro boundary conditions which means that the given mesh is repeated `2Nx+1`, `2Ny+1 and`2Nz+1`times in`x`,`y`and`z` direction, respectively.
