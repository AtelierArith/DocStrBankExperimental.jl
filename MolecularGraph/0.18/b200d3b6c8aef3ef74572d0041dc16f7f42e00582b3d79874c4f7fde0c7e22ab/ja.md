```
standard_weight_unc(atomsymbol::Symbol) -> Tuple{Float64,Float64}
standard_weight_unc(atom) -> Tuple{Float64,Float64}
standard_weight_unc(mol::MolGraph) -> Tuple{Float64,Float64}
```

標準原子量（または分子量）とその不確かさのタプルを返します。

`Atom.mass` が指定されている場合、原子の計算された正確な質量が代わりに使用されます。
