```
isotopiccomposition(atomsymbol::Symbol, number::Int; threshold=0.001
    ) -> Vector{Tuple{Float64,Float64}}
isotopiccomposition(mol::MolGraph; threshold=0.001
    ) -> Vector{Tuple{Float64,Float64}}
```

原子または分子の同位体組成を質量と組成のタプルのベクターとして返します。

指定された閾値よりも低い存在量の記録はフィルタリングされます（デフォルトは0.001 = 0.1%）。
