```
excitation(addr::OccupationNumberFS, c::NTuple, d::NTuple)
→ (nadd, α)
```

[`OccupationNumberFS`](@ref) に対して、Fock状態 `addr` にモード番号 `c` と `d` のタプルで指定された生成および消滅演算子を適用することで励起を生成します。モードは整数（1から始まる）または `BoseFSIndex` 型のインデックスでインデックス付けされます。値 `α` は、消滅前と生成後のモード占有数の積の平方根によって与えられます。

このタイプの励起によって粒子の数が変わることがあります。

# 例

```jl_doctest
julia> s = fs"|1 2 3⟩{8}"
OccupationNumberFS{3, UInt8}(1, 2, 3)

julia> num_particles(s)
6

julia> es, α = excitation(s, (1,1), (3,))
(OccupationNumberFS{3, UInt8}(3, 2, 2), 4.242640687119285)

julia> num_particles(es)
7
```
