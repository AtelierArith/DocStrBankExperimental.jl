Modification of [`MapFormat`](@ref).

During unpacking, the types and formats of future entries may depend on past entries via overloading [`iterstate`](@ref).

!!! info
    [`DynamicMapFormat`](@ref) is currently slower than [`MapFormat`](@ref), even if [`iterstate`](@ref) just enumerates indices. In principle, however, the compiler should have all information neccessary to optimize [`DynamicMapFormat`](@ref) in this case and bring the performance on par. In the future, we might thus deprecate [`DynamicMapFormat`](@ref) and absorb its functionality into [`MapFormat`](@ref).

