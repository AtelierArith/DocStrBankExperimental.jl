```
removable_hydrogens(mol::SimpleMolGraph{T,V,E}) -> Vector{T}
```

取り外し可能な水素ノードのベクターを返します。

取り外し可能な水素は、電荷がなく、未対電子がなく、特定の質量がなく、立体特異性がなく、有機重原子に結合しています。
