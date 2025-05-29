```
 is_subdomain(subdomain::BitVector, domain::BitVector)
 is_subdomain(subdomain::StateSparseSet, domain::BitVector)
```

`subdomain`が`domain`のサブドメインであるかどうかをチェックします。例: [0, 0, 1, 0] は [0, 1, 1, 1] のサブドメインです。
