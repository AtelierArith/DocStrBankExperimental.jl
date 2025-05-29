```
OneDGrid(dev::Device = CPU();
         nx, Lx,
         x0 = -Lx/2, nthreads = Sys.CPU_THREADS, effort = FFTW.MEASURE, 
         T = Float64, aliased_fraction = 1/3)
```

Construct a `OneDGrid` on `dev`ice; by default on `CPU()`. Grid size is `Lx`, resolution is `nx`,  and leftmost position is `x0`. FFT plans are generated for `nthreads` CPUs using FFTW flag `effort`. The float type is `T`. The `aliased_fraction` keyword determines the highest wavenubers that are being zero-ed out by `dealias!` function; 1/3 is the nominal value for quadratic nonlinearities. 
