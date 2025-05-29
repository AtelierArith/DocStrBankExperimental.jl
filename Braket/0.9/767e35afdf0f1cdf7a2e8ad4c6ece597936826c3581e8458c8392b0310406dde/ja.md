```
qubits(c::Circuit) -> QubitSet
```

`c` が定義されているすべての量子ビットを含む [`QubitSet`](@ref) を返します。

# 例

```jldoctest
julia> c = Circuit();

julia> H(c, 0);

julia> CNot(c, 0, 1);

julia> qubits(c)
QubitSet with 2 elements:
  0
  1
```
