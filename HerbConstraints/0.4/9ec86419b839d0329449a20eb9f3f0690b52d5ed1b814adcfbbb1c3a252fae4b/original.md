```
 is_subdomain(subdomain::BitVector, domain::BitVector)
 is_subdomain(subdomain::StateSparseSet, domain::BitVector)
```

Checks if `subdomain` is a subdomain of `domain`. Example: [0, 0, 1, 0] is a subdomain of [0, 1, 1, 1]
