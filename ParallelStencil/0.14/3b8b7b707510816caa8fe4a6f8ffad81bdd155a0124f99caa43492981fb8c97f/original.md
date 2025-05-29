Module ParallelStencil

Enables domain scientists to write high-level code for parallel high-performance stencil computations that can be deployed on both GPUs and CPUs.

# General overview and examples

https://github.com/omlins/ParallelStencil.jl

# Primary macros

  * [`@init_parallel_stencil`](@ref)
  * [`@parallel`](@ref)
  * [`@hide_communication`](@ref)
  * [`@zeros`](@ref)
  * [`@ones`](@ref)
  * [`@rand`](@ref)
  * [`@falses`](@ref)
  * [`@trues`](@ref)
  * [`@fill`](@ref)
  * [`@fill!`](@ref)

!!! note "Advanced"
      * [`@parallel_indices`](@ref)
      * [`@parallel_async`](@ref)
      * [`@synchronize`](@ref)


# Macros available for [`@parallel_indices`](@ref) kernels

  * [`@ps_show`](@ref)
  * [`@ps_println`](@ref)

!!! note "Advanced"
      * [`@gridDim`](@ref)
      * [`@blockIdx`](@ref)
      * [`@blockDim`](@ref)
      * [`@threadIdx`](@ref)
      * [`@sync_threads`](@ref)
      * [`@sharedMem`](@ref)


# Submodules

  * [`ParallelStencil.AD`](@ref)
  * [`ParallelStencil.FieldAllocators`](@ref)
  * [`ParallelStencil.FiniteDifferences1D`](@ref)
  * [`ParallelStencil.FiniteDifferences2D`](@ref)
  * [`ParallelStencil.FiniteDifferences3D`](@ref)

# Modules generated in caller

  * [`Data`](@ref)

!! note "Activation of GPU support"     The support for GPU (CUDA, AMDGPU or Metal) is provided with extensions and requires therefore an explicit installation of the corresponding packages (CUDA.jl, AMDGPU.jl or Metal.jl). Note that it is not required to import explicitly the corresponding module (CUDA, AMDGPU or Metal); this is automatically done by [`@init_parallel_stencil`](@ref).

To see a description of a macro or module type `?<macroname>` (including the `@`) or `?<modulename>`, respectively.
