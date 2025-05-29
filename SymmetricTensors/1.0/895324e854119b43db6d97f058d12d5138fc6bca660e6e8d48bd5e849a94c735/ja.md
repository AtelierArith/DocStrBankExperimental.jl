```
SymmetricTensor(data::Array, bls::Int)
```

`Array`から`SymmetricTensor`を構築します。

```jldoctest
julia> a = reshape(collect(1.:16.), 4, 4);

julia> SymmetricTensor(a*a')
SymmetricTensors.SymmetricTensor{Float64,2}(Union{Array{Float64,2}, Void}[[276.0 304.0; 304.0 336.0][332.0 360.0; 368.0 400.0]; nothing [404.0 440.0; 440.0 480.0]], 2, 2, 4, true)
```
