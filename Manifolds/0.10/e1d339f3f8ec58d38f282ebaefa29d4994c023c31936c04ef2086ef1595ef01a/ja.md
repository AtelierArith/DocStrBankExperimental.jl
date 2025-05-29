```
get_vector(M::OrthogonalMatrices, p, Xⁱ, B::DefaultOrthogonalBasis)
get_vector(M::Rotations, p, Xⁱ, B::DefaultOrthogonalBasis)
```

点 `p` における [`Rotations`](@ref) または [`OrthogonalMatrices`](@ref) のユニークな接ベクトル成分 `Xⁱ` を接ベクトルの行列表現 $X$ に変換します。使用される規約については [`get_coordinates`](@ref get_coordinates(::GeneralUnitaryMatrices, ::Any...)) を参照してください。
