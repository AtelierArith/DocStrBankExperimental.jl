```
excitation(addr::SingleComponentFockAddress, creations::NTuple, destructions::NTuple)
```

アドレス `addr` に対して、適切なアドレスインデックスのタプルである `creations` と `destructions` を適用することによって励起を生成します（すなわち、ボソンの場合は [`BoseFSIndex`](@ref)、フェルミオンの場合は [`FermiFSIndex`](@ref)）。

$$
a^†_{c_1} a^†_{c_2} \ldots a_{d_1} a_{d_2} \ldots |\mathrm{addr}\rangle \to
α|\mathrm{naddr}\rangle
$$

新しいアドレス `naddr` と因子 `α` を返します。`α` の値は、破壊前と生成後のモード占有数の積の平方根によって与えられます。励起が不正な場合は、任意のアドレスと値 `0.0` を返します。

# 例

```jldoctest
julia> f = FermiFS(1,1,0,0,1,1,1,1)
FermiFS{6,8}(1, 1, 0, 0, 1, 1, 1, 1)

julia> i, j, k, l = find_mode(f, (3,4,2,5))
(FermiFSIndex(occnum=0, mode=3, offset=2), FermiFSIndex(occnum=0, mode=4, offset=3), FermiFSIndex(occnum=1, mode=2, offset=1), FermiFSIndex(occnum=1, mode=5, offset=4))

julia> excitation(f, (i,j), (k,l))
(FermiFS{6,8}(1, 0, 1, 1, 0, 1, 1, 1), -1.0)
```

[`SingleComponentFockAddress`](@ref) を参照してください。
