```julia
fetchkernel(kernel; directory, ignorecache)

```

Given the ephemeris file name, download the file to the `SPICEKernels.jl` scratch space,  and return a path to the file location. If a full URL or path is provided, that path will  be used. Otherwise, the `kernel` is assumed to be a SPICE Generic Kernel. 

# Extended Help

If `ignorecache` is is enabled, the ephemeris file will be re-downloaded even if it exists already  in the `SPICEKernels.jl` scratch space. If `directory` is set to something other than the  `SPICEKernels.SPICE_KERNEL_DIR` variable, the file is downloaded to the provided directory  instead of the `SPICEKernels.jl` scratch space. 
