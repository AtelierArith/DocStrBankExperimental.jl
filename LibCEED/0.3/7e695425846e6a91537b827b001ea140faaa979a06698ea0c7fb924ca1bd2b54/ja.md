```
create_interior_qfunction(ceed::Ceed, name::AbstractString)
```

指定された名前を使用して、Q関数ギャラリーから[`QFunction`](@ref)を作成します。

# 例

  * 3D質量演算子を構築して適用する

```
build_mass_qf = create_interior_qfunction(c, "Mass3DBuild")
apply_mass_qf = create_interior_qfunction(c, "MassApply")
```

  * 3Dポアソン演算子を構築して適用する

```
build_poi_qf = create_interior_qfunction(c, "Poisson3DBuild")
apply_poi_qf = create_interior_qfunction(c, "Poisson3DApply")
```
