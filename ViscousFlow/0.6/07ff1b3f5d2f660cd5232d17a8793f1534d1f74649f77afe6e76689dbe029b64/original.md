```
setup_grid(xlim::Tuple,ylim::Tuple,phys_params::Dict[;nthreads_max=length(Sys.cpu_info())])
```

Construct a Cartesian grid with limits `xlim` and `ylim` and spacing determined by the Reynolds number in the `phys_params`. The maximum number of threads can be optionally set; it defaults to the number of processor cores.
