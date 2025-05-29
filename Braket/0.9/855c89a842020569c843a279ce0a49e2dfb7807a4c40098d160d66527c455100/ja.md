```
StateVector(c::Circuit) -> Circuit
```

`c`のすべてのキュービットに対して`StateVector`測定を構築し、それを[`Circuit`](@ref) `c`の結果として追加します。

# 例

```jldoctest
julia> c = Circuit();

julia> c = H(c, collect(0:3));

julia> c = StateVector(c);
```
