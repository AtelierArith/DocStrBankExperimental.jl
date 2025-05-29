```julia
is_geminal(
    a1::BiochemicalAlgorithms.Atom,
    a2::BiochemicalAlgorithms.Atom
) -> Union{Missing, Bool}

```

二つの原子がジェミナルであるかどうかを決定します。

二つの原子がジェミナルであるのは、共通の結合を持たず、両方が第三の原子に結合している場合です。例えば、水中の二つの水素原子はジェミナルです。水素結合（`has_flag(bond, :TYPE__HYDROGEN)`）は無視されます。
