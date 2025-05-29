```
status = finufft_destroy!(plan::finufft_plan{T}) where T <: finufftReal
```

This destroys a FINUFFT plan object: it deallocates all stored FFTW plans, nonuniform point sorting arrays, kernel Fourier transforms arrays, and any other allocations, and nulls the plan pointer.

An integer status code is returned, that is 0 if successful. If one attempts to destroy an already-destroyed plan, 1 is returned (see FINUFFT documentation for finufft_destroy).
