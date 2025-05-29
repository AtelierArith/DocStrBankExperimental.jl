```
orthogonality(B)
```

基底 `B` の [`BasisOrthogonality`](@ref) 特性を返します。

# 例

```julia
julia> orthogonality(BSpline(LinearKnotSet(7, 0, 1, 11)))
CompactBases.NonOrthogonal()

julia> orthogonality(FEDVR(range(0, stop=1, length=11), 7))
CompactBases.Orthonormal()

julia> orthogonality(StaggeredFiniteDifferences(0.1, 0.3, 0.1, 10.0))
CompactBases.Orthonormal()

julia> orthogonality(FiniteDifferences(range(0, stop=1, length=11)))
CompactBases.Orthogonal()
```
