```
SparseTensor(I::Union{PyObject,Array{T,1}}, J::Union{PyObject,Array{T,1}}, V::Union{Array{Float64,1}, PyObject}, m::Union{S, PyObject, Nothing}=nothing, n::Union{S, PyObject, Nothing}=nothing) where {T<:Integer, S<:Integer}
```

スパーステンソルを構築します。例:

```
ii = [1;2;3;4]
jj = [1;2;3;4]
vv = [1.0;1.0;1.0;1.0]
s = SparseTensor(ii, jj, vv, 4, 4)
s = SparseTensor(sprand(10,10,0.3))
```
