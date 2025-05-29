```
OccupiedModeMap(addr) <: AbstractVector
```

アドレス内の占有モードのマップを、[`excitation`](@ref) - [`BoseFSIndex`](@ref) または [`FermiFSIndex`](@ref) と互換性のあるインデックスの `AbstractVector` として取得します。

`OccupiedModeMap(addr)[i]` には、`i` 番目の占有モードのインデックスが含まれています。これは、[`find_occupied_mode`](@ref) を使って占有モードを繰り返し探すのが時間がかかる可能性があるため便利です。`OccupiedModeMap(addr)` は、[`occupied_modes`](@ref) が返すイテレータのイーガー版です。これは [`onr`](@ref) に似ていますが、より多くの情報を含んでいます。

# 例

```jldoctest
julia> b = BoseFS(10, 0, 0, 0, 2, 0, 1)
BoseFS{13,7}(10, 0, 0, 0, 2, 0, 1)

julia> mb = OccupiedModeMap(b)
3-element OccupiedModeMap{7, BoseFSIndex}:
 BoseFSIndex(occnum=10, mode=1, offset=0)
 BoseFSIndex(occnum=2, mode=5, offset=14)
 BoseFSIndex(occnum=1, mode=7, offset=18)

julia> f = FermiFS(1,1,1,1,0,0,1,0,0)
FermiFS{5,9}(1, 1, 1, 1, 0, 0, 1, 0, 0)

julia> mf = OccupiedModeMap(f)
5-element OccupiedModeMap{5, FermiFSIndex}:
 FermiFSIndex(occnum=1, mode=1, offset=0)
 FermiFSIndex(occnum=1, mode=2, offset=1)
 FermiFSIndex(occnum=1, mode=3, offset=2)
 FermiFSIndex(occnum=1, mode=4, offset=3)
 FermiFSIndex(occnum=1, mode=7, offset=6)

julia> mf == collect(occupied_modes(f))
true

julia> dot(mf, mb)
11

julia> dot(mf, 1:20)
17
```

[`dot`](@ref Main.Hamiltonians.dot) や [`SingleComponentFockAddress`](@ref) も参照してください。
