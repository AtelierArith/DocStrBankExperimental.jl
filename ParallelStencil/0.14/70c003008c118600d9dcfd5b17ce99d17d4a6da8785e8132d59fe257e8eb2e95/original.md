```
@parallel kernel
@parallel inbounds=... memopt=... ndims=... kernel
```

Declare the `kernel` parallel and containing stencil computations be performed with one of the submodules `ParallelStencil.FiniteDifferences{1D|2D|3D}` (or with a compatible custom module or set of macros).

# Optional keyword arguments

  * `inbounds::Bool`: whether to apply `@inbounds` to the kernel. The default is `false` or as set with the `inbounds` keyword argument of [`@init_parallel_stencil`](@ref).
  * `memopt::Bool=false`: whether to perform advanced stencil-specific on-chip memory optimisations. If `memopt=true` is set, then it must also be set in the corresponding kernel call(s).

!!! note "Advanced optional keyword arguments"
      * `ndims::Integer|Tuple`: the number of dimensions used for the stencil computations in the kernels: 1, 2 or 3 (or a tuple containing any of the previous in order to generate a method for each of the given values - this can only work correctly if the macros used *and loaded* work for any of the chosen values of `ndims`!). A default can be set with the `ndims` keyword argument of [`@init_parallel_stencil`](@ref). The keyword argument `N` becomes mandatory when `ndims` is a tuple in order to dispatch on the number of dimensions (see below).
      * `N::Integer|Tuple`: the value(s) a type parameter `N` in the kernel method signatures must take. The values are typically computed based on `ndims` (set with the corresponding keyword argument of the `@parallel` macro or `@init_parallel_stencil`), which will be substituted in the expression before evaluating it. This enables dispatching on the number of dimensions in the kernel methods (e.g., `@parallel ndims=(1,3) N=ndims function f(A::Data.Array{N}) ... end`). The keyword argument `N` is mandatory if `ndims` is a tuple and must then furthermore be a tuple of the same length as `ndims`.


See also: [`@init_parallel_stencil`](@ref)

---

```
@parallel kernelcall
@parallel memopt=... kernelcall
@parallel ∇=... kernelcall
@parallel ∇=... memopt=... kernelcall
```

!!! note "Advanced"
    ```
    @parallel ranges kernelcall
    @parallel nblocks nthreads kernelcall
    @parallel ranges nblocks nthreads kernelcall
    @parallel (...) memopt=... configcall=... backendkwargs... kernelcall
    @parallel ∇=... ad_mode=... ad_annotations=... (...) memopt=... backendkwargs... kernelcall
    ```


Declare the `kernelcall` parallel. The kernel will automatically be called as required by the package for parallelization selected with [`@init_parallel_kernel`](@ref). Synchronizes at the end of the call (if a stream is given via keyword arguments, then it synchronizes only this stream). The keyword argument `∇` triggers a parallel call to the gradient kernel instead of the kernel itself. The automatic differentiation is performed with the package Enzyme.jl (refer to the corresponding documentation for Enzyme-specific terms used below); Enzyme needs to be imported before ParallelStencil in order to have it load the corresponding extension.

# Arguments

  * `kernelcall`: a call to a kernel that is declared parallel.

!!! note "Advanced optional arguments"
      * `ranges::Tuple{UnitRange{},UnitRange{},UnitRange{}} | Tuple{UnitRange{},UnitRange{}} | Tuple{UnitRange{}} | UnitRange{}`: the ranges of indices in each dimension for which computations must be performed.
      * `nblocks::Tuple{Integer,Integer,Integer}`: the number of blocks to be used if the package CUDA, AMDGPU or Metal was selected with [`@init_parallel_kernel`](@ref).
      * `nthreads::Tuple{Integer,Integer,Integer}`: the number of threads to be used if the package CUDA, AMDGPU or Metal was selected with [`@init_parallel_kernel`](@ref).


# Keyword arguments

  * `memopt::Bool=false`: whether the kernel to be launched was generated with `memopt=true` (meaning the keyword was set in the kernel declaration).

!!! note "Advanced"
      * `∇`: the variable(s) with respect to which the kernel is to be differentiated automatically and a duplicate for each variable to store the result in, separated by `->`, e.g., `∇=(A->Ā, B->B̄)`. Setting this keyword triggers a parallel call to the gradient kernel instead of the kernel itself. The duplicate variables are by default passed to Enzyme with the annotation `DuplicatedNoNeed`, e.g., `DuplicatedNoNeed(A, Ā)`. Use the keyword argument `ad_annotations` to modify this behavior.
      * `ad_mode=Enzyme.Reverse`: the automatic differentiation mode (see the documentation of Enzyme.jl for more information).
      * `ad_annotations=()`: Enzyme variable annotations for automatic differentiation in the format `(<keyword>=<variable(s)>, <keyword>=<variable(s)>, ...)`, where `<variable(s)>` can be a single variable or a tuple of variables (e.g., `ad_annotations=(Duplicated=B, Active=(a,b))`). Currently supported annotations are: (:Const, :Active, :Duplicated, :DuplicatedNoNeed).
      * `configcall=kernelcall`: a call to a kernel that is declared parallel, which is used for determining the kernel launch parameters. This keyword is useful, e.g., for generic automatic differentiation using the low-level submodule [`AD`](@ref).
      * `backendkwargs...`: keyword arguments to be passed further to CUDA, AMDGPU or Metal (ignored for Threads and Polyester).


!!! note "Performance note"
    Kernel launch parameters are automatically defined with heuristics, where not defined with optional kernel arguments. For CUDA and AMDGPU, `nthreads` is typically set to (32,8,1) and `nblocks` accordingly to ensure that enough threads are launched.


See also: [`@init_parallel_kernel`](@ref)
