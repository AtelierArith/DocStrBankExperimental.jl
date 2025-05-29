```
find_mode(::SingleComponentFockAddress, i)
```

アドレス内の `i` 番目のモードを見つけます。 [`BoseFS`](@ref) に対しては [`BoseFSIndex`](@ref) を、[`FermiFS`](@ref) に対しては [`FermiFSIndex`](@ref) を返します。モードのタプルでも動作します。境界チェックは行いません。

```jldoctest
julia> find_mode(BoseFS(1, 0, 2), 2)
BoseFSIndex(occnum=0, mode=2, offset=2)

julia> find_mode(FermiFS(1, 1, 1, 0), (2,3))
(FermiFSIndex(occnum=1, mode=2, offset=1), FermiFSIndex(occnum=1, mode=3, offset=2))
```

[`SingleComponentFockAddress`](@ref) を参照してください。
