```
randmps(physdims::Dims{N}, Dmax::Int, T::Type{<:Number} = Float64) where {N}
```

Construct a random, right-normalised MPS with local Hilbert space dimensions given by `physdims` and max bond-dimension given by `Dmax`. 

`T` specifies the element type, eg. use `T=ComplexF64` for a complex valued MPS.
