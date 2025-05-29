```
deleteat!(sites::AtomList, indices...)
```

指定されたインデックス/インデックスのリストを介して、`sites`から原子を削除します。

削除後に`sites`が表示されると、原子は適切な整数の順序を維持するために再番号付けされます。たとえば、"1,2,3,4"と番号付けされた原子のシーケンスがある場合、原子3が削除されると、新しい順序は"1,2,3"になります。

```jldoctest; setup=:(using BloqadeLattices)
julia> sites = generate_sites(SquareLattice(), 2, 2, scale=6.7)
4-element AtomList{2, Float64}:
 (0.0, 0.0)
 (6.7, 0.0)
 (0.0, 6.7)
 (6.7, 6.7)

julia> deleteat!(sites, 2, 3)
2-element AtomList{2, Float64}:
 (0.0, 0.0)
 (6.7, 6.7)
```
