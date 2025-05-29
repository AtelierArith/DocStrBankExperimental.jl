```
lift(M::smodule{T}, SM::smodule{T}, goodShape::Bool, isSB::Bool, divide::Bool) where T
```

Represents the generators of `SM` in terms of the generators of `M`. Returns `(result, rest, U)` with     `Matrix(SM)*U - Matrix(rest) = Matrix(M)*Matrix(result)` If `SM` is in `M`, then `rest` is the null module. Otherwise, `rest = SM` if `!divide`, and `rest = normalform(SM, std(M))` if `divide`. `U` is a diagonal matrix of units, differing from the identity matrix only for local ring orderings.

There are three boolean options. `goodShape`: maximal non-zero index in generators of `SM` <= that of `M`, which should be come from a rank check `rank(SM)==rank(M)`. `isSB`: generators of `M` form a Groebner basis. `divide`: allow `SM` not to be a submodule of `M`.
