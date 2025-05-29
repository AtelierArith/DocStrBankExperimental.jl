```
AdjointGradient(c::Circuit, o::Observable, targets, parameters) -> Circuit
```

`o` の期待値に関する `AdjointGradient` 計算を構築し、ターゲットの量子ビット `targets` に対して `parameters` の部分導関数を計算し、[`Circuit`](@ref) `c` に結果として追加します。

`o` は任意の `Observable` である可能性があります。`targets` は `QubitSet` の `Vector` でなければならず（`o` が `Sum` でない場合は単一の `QubitSet`）、それぞれが `o` の対応する項の量子ビット数と同じ長さである必要があります。`parameters` には [`FreeParameter`](@ref) または `String` の要素、または `["all"]` を含むことができる場合、この場合は回路内のすべてのパラメータに関して勾配が計算されます。

# 例

```jldoctest
julia> c = Circuit();

julia> α = FreeParameter("alpha");

julia> c = H(c, collect(0:10));

julia> c = Rx(c, collect(0:10), α);

julia> c = AdjointGradient(c, Braket.Observables.Z(), 0, [α]);
```
