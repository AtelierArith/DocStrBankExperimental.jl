`Pipeline` is a type for tuples holding conditioners.

A pipeline holds a sequence of conditioners learned and (optionally) applied using [`fit!`](@ref). It can be  subsequently applied on other data as it has been learnt  using the [`transform!`](@ref) function. All `fit!` methods return a pipeline.

Pipelines comprising a single conditioner are allowed.

Pipelines can be saved to a file using the [`saveas`](@ref) function and loaded from a file using the [`load`](@ref) function.

Note that in Julia tuples are immutable, thus it is not possible to modify a pipeline. However it is possible to change the fields of the conditioners  it holds.

In order to create a pipeline use the [`@pipeline`](@ref) macro.

**See also**: [`fit!`](@ref), [`transform!`](@ref)
