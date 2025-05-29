```
DensityMatrix(c::Circuit, targets) -> Circuit
```

`targets`に対して`DensityMatrix`測定を構築し、それを[`Circuit`](@ref) `c`の結果として追加します。

`targets`は次のいずれかである可能性があります：

  * [`QubitSet`](@ref)
  * `Int`の`Vector`および/または[`Qubit`](@ref)
  * `Int`または`Qubit`
  * 省略された場合、測定は`c`のすべての量子ビットに適用されます。

# 例

```jldoctest
julia> c = Circuit();

julia> c = H(c, collect(0:3));

julia> c = DensityMatrix(c, 2);
```
