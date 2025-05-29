```
System(mb[; T])
```

与えられた多体基底 `mb` を持つシステムを作成します。

この関数は、格子を持つ任意の多体基底から多体システムを作成するために使用されます。

## 例

```jldoctest
julia> using LatticeModels

julia> lat = SquareLattice(3, 3);

julia> bas = SpinBasis(1//2) ⊗ LatticeBasis(lat);

julia> mbas = ManyBodyBasis(bas, fermionstates(bas, 2));

julia> System(mbas, T=2)
多体システム (2D空間の9サイトの正方格子) ⊗ スピン(1/2) (153状態, T=2.0)
```
