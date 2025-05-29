ComputationalResources makes it possible to dispatch to different methods that employ different computational resources. The exported resources are:

  * `CPU1` (single-threaded computation)
  * `CPUThreads` (multi-threaded computation)
  * `CPUProcesses` (multi-process computation)
  * `ArrayFireLibs` (using the [ArrayFire package](https://github.com/JuliaComputing/ArrayFire.jl)
  * `CUDALibs` (GPU computation using NVIDIA's CUDA libraries)
  * `OpenCLLibs` (GPU computation using the OpenCL libraries)

There are also functions that interact with package initialization machinery to control the availability of supported methods:

  * `addresource(T)`: request newly-loaded packages to support resource `T`
  * `rmresource(T)`: stop asking newly-loaded packages to support resource `T`
  * `haveresource(T)`: test whether resource `T` has been requested
