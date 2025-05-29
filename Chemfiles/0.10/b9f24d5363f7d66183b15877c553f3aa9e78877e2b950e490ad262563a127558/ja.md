```julia
vdw_radius(atom::Chemfiles.Atom) -> Float64

```

`atom`の原子タイプからファン・デル・ワールス半径を取得します。

半径が見つからない場合、この関数は0を返します。
