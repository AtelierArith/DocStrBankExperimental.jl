```
ThreeDGrid(dev::Device=CPU(); nx, Lx, ny=nx, Ly=Lx, nz=nx, Lz=Lx,
           x0=-Lx/2, y0=-Ly/2, z0=-Lz/2,
           nthreads=Sys.CPU_THREADS, effort=FFTW.MEASURE, T=Float64,
           aliased_fraction=1/3)
```

Construct a `ThreeDGrid` on `dev`ice; by default on `CPU()`. Grid size is `Lx`, `Ly`, `Lz`, resolution is `nx`, `ny`, `nz` and leftmost positions are `x0`, `y0`, `z0`. FFT plans are generated for `nthreads` CPUs using FFTW flag `effort`. The float type is `T`. The `aliased_fraction` keyword determines the highest wavenubers that are being zero-ed out by `dealias!` function; 1/3 is the nominal value for quadratic nonlinearities. 
