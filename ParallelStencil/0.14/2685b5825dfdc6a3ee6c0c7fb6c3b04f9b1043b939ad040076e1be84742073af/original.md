@parallel*async kernelcall @parallel*async ∇=... kernelcall

!!! note "Advanced"
    ```
    @parallel_async ranges kernelcall
    @parallel_async nblocks nthreads kernelcall
    @parallel_async ranges nblocks nthreads kernelcall
    @parallel_async (...) configcall=... backendkwargs... kernelcall
    @parallel_async ∇=... ad_mode=... ad_annotations=... (...) backendkwargs... kernelcall
    ```


Declare the `kernelcall` parallel as with [`@parallel`](@ref) (see [`@parallel`](@ref) for more information); deactivates however automatic synchronization at the end of the call. Use [`@synchronize`](@ref) for synchronizing.

!!! note "Performance note"
    @parallel*async falls currently back to running synchronously if the package Threads or Polyester was selected with [`@init*parallel_stencil`](@ref).


See also: [`@synchronize`](@ref), [`@parallel`](@ref)
