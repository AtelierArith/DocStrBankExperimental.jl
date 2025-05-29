```
enableAcceleration(tsg::TasmanianSG, acceleration_type, GPUID = 0)
```

Enables the use of accelerated backend libraries and extensions, such as BLAS and CUDA. Each acceleration type requires corresponding CMake compile options, otherwise the backend will fallback to the closest available options.

sAccelerationType: string

'none'       core fallback mode, relies on sequential implementation       if compiled with Tasmanian*ENABLE*OPENMP this will use       simple "omp parallel for" to take advantage of multiple cpu cores

'cpu-blas'       uses BLAS level 2 and 3 functions for acceleration of batch       evaluations       requires Tasmanian*ENABLE*BLAS=ON       this is the default mode, if available

'gpu-default'       uses CUDA kernels, cuBlas, cuSparse and MAGMA libraries for       accelerated matrix operations, e.g., cublasDgemm       refer to TasGrid::TypeAcceleration for more details

'gpu_cublas'       uses the Nvidia cuBlas and cuSparse libraries

'gpu-cuda'       uses custom CUDA kernels in addition to the accelerated       linear algebra libraries

'gpu-magma'       uses the custom CUDA kernels and the MAGMA library in place       of the default Nvidia libraries

GPUID: integer       indicates the GPU device to use, if set to None then device       zero will be used first or the device set with setGPUID()
