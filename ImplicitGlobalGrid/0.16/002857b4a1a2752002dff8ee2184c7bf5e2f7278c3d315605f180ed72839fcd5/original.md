```
update_halo!(A)
update_halo!(A...)
```

!!! note "Advanced"
    ```
    update_halo!(A, B, (A=C, halowidths=..., (A=D, halowidths=...), ...)
    ```


Update the halo of the given GPU/CPU-array(s).

# Typical use cases:

```
update_halo!(A)                                # Update the halo of the array A.
update_halo!(A, B, C)                          # Update the halos of the arrays A, B and C.
update_halo!(A, B, (A=C, halowidths=(2,2,2)))  # Update the halos of the arrays A, B, C, defining non default halowidth for C.
```

!!! note "Performance note"
    Group subsequent calls to `update_halo!` in a single call for better performance (enables additional pipelining).


!!! note "Performance note"
    If the system supports CUDA-aware MPI (for Nvidia GPUs) or ROCm-aware MPI (for AMD GPUs), it may be activated for ImplicitGlobalGrid by setting one of the following environment variables (at latest before the call to `init_global_grid`):

    ```shell
    shell> export IGG_CUDAAWARE_MPI=1
    ```

    ```shell
    shell> export IGG_ROCMAWARE_MPI=1
    ```

