```
pointgroup(ops:AbstractVector{SymOperation{D}})
pointgroup(sg::AbstractGroup)
```

Computes the point group associated with a space group `sg` (characterized by a set of operators `ops`, which, jointly with lattice translations generate  the space group), obtained by "taking away" any translational parts and  then reducing to the resulting unique rotational operations. (technically, in the language of Bradley & Cracknell, this is the so-called isogonal point group of `sg`; see Sec. 1.5).

Returns a `Vector` of `SymOperation`s.
