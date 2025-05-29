```
SymmetricIntervalHull{N, S<:LazySet{N}} <: AbstractHyperrectangle{N}
```

Type that represents the symmetric interval hull of a compact set.

### Fields

  * `X`     – compact set
  * `cache` – partial storage of already computed bounds, organized as mapping            from the dimension to the bound value

### Notes

The symmetric interval hull can be computed with $2n$ support-function queries (of unit vectors), where $n$ is the dimension of the wrapped set (i.e., two queries per dimension). When asking for the support vector (or support function) in a direction $d$, one needs $2k$ such queries, where $k$ is the number of non-zero entries in $d$.

However, if one asks for many support vectors (or support-function evaluations) in a loop, the number of computations may exceed $2n$. To be most efficient in such cases, this type stores the intermediately computed bounds in the `cache` field.

The set `X` must be bounded. The flag `check_boundedness` (which defaults to `true`) can be used to elide the boundedness check in the inner constructor. Misuse of this flag can result in incorrect behavior.

The symmetric interval hull of a set is a hyperrectangle centered in the origin, which in particular is convex.

An alias for this function is `⊡`.
