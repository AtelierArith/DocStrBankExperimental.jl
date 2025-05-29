```julia
is_vicinal(
    a1::BiochemicalAlgorithms.Atom,
    a2::BiochemicalAlgorithms.Atom
) -> Bool

```

二つの原子が隣接しているかどうかを決定します。

二つの原子は、三つの結合（1-4位置）で隔てられている場合に隣接しています。水素結合（`has_flag(bond, :TYPE__HYDROGEN)`）は無視されます。
