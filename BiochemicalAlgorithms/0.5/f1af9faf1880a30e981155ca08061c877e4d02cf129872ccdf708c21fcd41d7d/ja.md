```
parent_system(::Atom)
parent_system(::Bond)
parent_system(::Chain)
parent_system(::SecondaryStructure)
parent_system(::Fragment)
parent_system(::Molecule)
parent_system(::System)
```

与えられたオブジェクトを含む `System{T}` を返します。 [`Base.parent`](@ref Base.parent(::System)) のエイリアスです。
