```
exact_mass_unc(atomsymbol::Symbol, [number::Union{Int, Nothing}]) -> Tuple{Float64,Float64}
exact_mass_unc(atom) -> Tuple{Float64,Float64}
exact_mass_unc(mol::MolGraph) -> Tuple{Float64,Float64}
```

計算された正確な質量とその不確実性のタプルを返します。

`number`が指定されていない場合や`Atom.mass`が指定されていない場合は、単一同位体質量が代わりに使用されます。
