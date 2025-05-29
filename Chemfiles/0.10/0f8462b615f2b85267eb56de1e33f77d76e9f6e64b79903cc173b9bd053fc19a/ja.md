```julia
covalent_radius(atom::Chemfiles.Atom) -> Float64

```

原子のタイプから`atom`の共有半径を取得します。

半径が見つからない場合は、0を返します。
