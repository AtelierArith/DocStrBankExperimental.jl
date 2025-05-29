```
destructure(model) -> vector, reconstructor
```

Copies all [`trainable`](@ref Optimisers.trainable), [`isnumeric`](@ref Optimisers.isnumeric) parameters in the model to a vector, and returns also a function which reverses this transformation. Differentiable.

# Example

```jldoctest
julia> v, re = destructure((x=[1.0, 2.0], y=(sin, [3.0 + 4.0im])))
(ComplexF64[1.0 + 0.0im, 2.0 + 0.0im, 3.0 + 4.0im], Restructure(NamedTuple, ..., 3))

julia> re([3, 5, 7+11im])
(x = [3.0, 5.0], y = (sin, ComplexF64[7.0 + 11.0im]))
```

If `model` contains various number types, they are promoted to make `vector`, and are usually restored by `Restructure`. Such restoration follows the rules  of `ChainRulesCore.ProjectTo`, and thus will restore floating point precision, but will permit more exotic numbers like `ForwardDiff.Dual`.

If `model` contains only GPU arrays, then `vector` will also live on the GPU. At present, a mixture of GPU and ordinary CPU arrays is undefined behaviour.
