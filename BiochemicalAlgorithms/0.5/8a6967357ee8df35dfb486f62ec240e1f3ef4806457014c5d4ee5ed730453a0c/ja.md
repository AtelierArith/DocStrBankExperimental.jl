```julia
is_bound_to(
    a1::BiochemicalAlgorithms.Atom,
    a2::BiochemicalAlgorithms.Atom
) -> Bool

```

二つの原子が互いに結合しているかどうかを決定します。水素結合（`has_flag(bond, :TYPE__HYDROGEN)`）は無視されます。
