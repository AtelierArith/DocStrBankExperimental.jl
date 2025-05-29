```
@parallel_indices indices kernel
@parallel_indices indices inbounds=... memopt=... ndims=... kernel
```

Declare the `kernel` parallel and generate the given parallel `indices` inside the `kernel` using the package for parallelization selected with [`@init_parallel_stencil`](@ref).

# Optional keyword arguments

```
- `inbounds::Bool`: whether to apply `@inbounds` to the kernel. The default is `false` or as set with the `inbounds` keyword argument of [`@init_parallel_stencil`](@ref).
- `memopt::Bool=false`: whether to perform advanced stencil-specific on-chip memory optimisations. If `memopt=true` is set, then it must also be set in the corresponding kernel call(s).
!!! note "Advanced optional keyword arguments"
    - `ndims::Integer|Tuple`: the number of indexing dimensions desired when using splat syntax for the `indices`: 1, 2, 3 (a default `ndims` value can be set with the corresponding keyword argument of [`@init_parallel_stencil`](@ref)) or a tuple containing any of the previous in order to generate a method for each of the given `ndims` values. Concretely, the splat syntax (e.g., `@parallel_indices (I...) ndims=(2,3) ...`) generates a tuple of parallel indices (`I` in this example) where the length is given by the `ndims` value (here `2` for the first method and `3` for the second). This makes it possible to write kernels that are agnostic to the number of dimensions (writing, e.g., `A[I...]` to access elements of the array `A`). The keyword argument `N` becomes mandatory when `ndims` is a tuple in order to dispatch on the number of dimensions (see below).
    - `N::Integer|Tuple`: the value(s) a type parameter `N` in the kernel method signatures must take. The values are typically computed based on `ndims` (set with the corresponding keyword argument of the `@parallel_indices` macro or `@init_parallel_stencil`), which will be substituted in the expression before evaluating it. This enables dispatching on the number of dimensions in the kernel methods (e.g., `@parallel_indices (I...) ndims=(1,3) N=ndims function f(A::Data.Array{N}) ... end`). The keyword argument `N` is mandatory if `ndims` is a tuple and must then furthermore be a tuple of the same length as `ndims`.
```

See also: [`@init_parallel_stencil`](@ref)
