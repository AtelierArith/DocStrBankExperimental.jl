```
isreal(v::PVector{T}, tol::Real)
```

Check whether there exists a fully real representative of `v`. For this `v` is first normalized, and then the largest entry in each component is made real. If after this the imaginary part of every coordinate is less than `tol` the vector is considered real.

## Example

```julia
julia> a, b = rand(ComplexF64, 2);
julia> v = PVector(a .* [1,2,3]) × PVector(b .* [4, 5]);
julia> isreal(v, 1e-6)
true
```
