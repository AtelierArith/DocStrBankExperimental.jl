```
CubicGrid(dims::NTuple{D,Int}, fold::NTuple{D,Bool})
```

`D`次元グリッドを表します。キュービックラティスといくつかの[`AbstractHamiltonian`](@ref)の境界条件を定義するために使用されます。例えば、[`HubbardRealSpace`](@ref)を構築する際のキーワード引数`geometry`で使用されます。この型のインスタンスは、直交ベクトルインデックス（タプルまたは`SVector`）と線形インデックス（整数）との間で変換するために使用できます。ベクトルでインデックス付けされた場合、境界外の次元が周期的であればグリッドに戻し、そうでなければ0にします（以下の例を参照）。

  * `dims`は各次元におけるグリッドのサイズを制御します。
  * `fold`は各次元の境界が周期的であるか（または運動量空間の場合は折りたたまれるか）を制御します。

```julia
julia> geo = CubicGrid((2,3), (true,false))
CubicGrid{2}((2, 3), (true, false))

julia> geo[1]
(1, 1)

julia> geo[2]
(2, 1)

julia> geo[3]
(1, 2)

julia> geo[(1,2)]
3

julia> geo[(3,2)] # 3は1に折りたたまれます
3

julia> geo[(3,3)]
5

julia> geo[(3,4)] # 範囲外の場合は0を返します
0
```

特別なケースのコンストラクタについては、[`PeriodicBoundaries`](@ref)、[`HardwallBoundaries`](@ref)、および[`LadderBoundaries`](@ref)も参照してください。また、[`HubbardRealSpace`](@ref)および[`G2RealSpace`](@ref)も参照してください。
