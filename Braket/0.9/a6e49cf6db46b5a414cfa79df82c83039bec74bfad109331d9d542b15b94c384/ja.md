```
Braket.Sample(c::Circuit, o, targets) -> Circuit
Braket.Sample(c::Circuit, o) -> Circuit
```

観測量 `o` をターゲットの量子ビット `targets` に対して `Braket.Sample` を構築し、[`Circuit`](@ref) `c` に結果として追加します。

`o` は次のいずれかである可能性があります：

  * 任意の [`Observable`](@ref Braket.Observables.Observable)
  * `Observable` に対応する `String`（例："x"）
  * 各要素が `Observable` に対応する `Vector{String}`

`targets` は次のいずれかである可能性があります：

  * [`QubitSet`](@ref)
  * `Int` の `Vector` および/または [`Qubit`](@ref)
  * `Int` または `Qubit`
  * 省略された場合、観測量 `o` は単一の量子ビットの観測量である限り、すべての量子ビットに適用されます。

# 例

```jldoctest
julia> c = Circuit();

julia> c = H(c, collect(0:10));

julia> c = Braket.Sample(c, Braket.Observables.Z(), 0);

julia> c = Braket.Sample(c, Braket.Observables.X());
```
