Inclusion(domain)

Represents the inclusion operator of a domain (that is, a type that overrides in) as an AbstractQuasiVector. That is, if `v = Inclusion(domain)`, then `v[x] == x` if `x in domain`, otherwise it throws a `DomainError`.

Inclusions are useful for turning domains into axes. They also serve the same role as `Slice` does for offset arrays.
