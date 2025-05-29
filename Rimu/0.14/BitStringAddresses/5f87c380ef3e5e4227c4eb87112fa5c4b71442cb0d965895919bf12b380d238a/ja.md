```
OccupiedPairsMap(addr::SingleComponentFockAddress) <: AbstractVector
```

`addr`内のすべての異なるインデックスのペアのマップを取得します。重複占有モードを含むペアは一度だけカウントされます（自己ペアリングを含む）。これは、例えば相互作用のための粒子ペアを特定することが明確でない場合や、即座に行うのが効率的でない場合に便利です。これは、`excitation`に渡すことができる粒子インデックスのタプルの要素を持つイagerイテレータです。

# 例

```jldoctest
julia> addr = BoseFS(10, 0, 0, 0, 2, 0, 1)
BoseFS{13,7}(10, 0, 0, 0, 2, 0, 1)

julia> pairs = OccupiedPairsMap(addr)
5-element OccupiedPairsMap{78, Tuple{BoseFSIndex, BoseFSIndex}}:
 (BoseFSIndex(occnum=10, mode=1, offset=0), BoseFSIndex(occnum=10, mode=1, offset=0))
 (BoseFSIndex(occnum=2, mode=5, offset=14), BoseFSIndex(occnum=2, mode=5, offset=14))
 (BoseFSIndex(occnum=2, mode=5, offset=14), BoseFSIndex(occnum=10, mode=1, offset=0))
 (BoseFSIndex(occnum=1, mode=7, offset=18), BoseFSIndex(occnum=10, mode=1, offset=0))
 (BoseFSIndex(occnum=1, mode=7, offset=18), BoseFSIndex(occnum=2, mode=5, offset=14))

julia> excitation(addr, pairs[2], pairs[4])
(BoseFS{13,7}(9, 0, 0, 0, 4, 0, 0), 10.954451150103322)
```

[`OccupiedModeMap`](@ref)も参照してください。
