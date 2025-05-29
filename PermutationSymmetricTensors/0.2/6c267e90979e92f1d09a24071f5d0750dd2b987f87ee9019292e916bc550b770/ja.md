SymmetricTensor(data::Array{T, 1}, ::Val{N}, ::Val{dim}) where {T, N, dim}

SymmetricTensor型の低レベルコンストラクタ。

```
例:

N = 10
dim = 3
Ndata = find_symmetric_tensor_size(N, dim)
T = Float64
data = rand(T, Ndata)
SymmetricTensor(data, Val(N), Val(dim))
```
