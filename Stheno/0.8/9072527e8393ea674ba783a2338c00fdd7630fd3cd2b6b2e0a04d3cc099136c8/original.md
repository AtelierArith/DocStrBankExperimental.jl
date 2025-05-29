```
BlockData{T, TV<:AbstractVector{T}, TX<:AbstractVector{TV}} <: AbstractVector{T}
```

A strictly ordered collection of `AbstractVector`s, representing a ragged array of data.

Very useful when working with `GPPP`s. For example

```julia
f = @gppp let
    f1 = GP(SEKernel())
    f2 = GP(Matern52Kernel())
    f3 = f1 + f2
end

# Specify a `BlockData` set that can be used to index into
# the `f2` and `f3` processes in `f`.
x = BlockData(
    GPPPInput(:f2, randn(4)),
    GPPPInput(:f3, randn(3)),
)

# Index into `f` at the input.
f(x)
```
