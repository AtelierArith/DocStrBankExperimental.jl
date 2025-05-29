Modification of [`VectorFormat`](@ref).

During unpacking, the types and formats of future entries may depend on past entries via overloading [`iterstate`](@ref).

!!! info
    [`DynamicVectorFormat`](@ref) is currently slower than [`VectorFormat`](@ref), even if [`iterstate`](@ref) just enumerates indices. In principle, however, the compiler should have all information neccessary to optimize [`DynamicVectorFormat`](@ref) in this case and bring the performance on par. In the future, we might thus deprecate [`DynamicVectorFormat`](@ref) and absorb its functionality into [`VectorFormat`](@ref).

