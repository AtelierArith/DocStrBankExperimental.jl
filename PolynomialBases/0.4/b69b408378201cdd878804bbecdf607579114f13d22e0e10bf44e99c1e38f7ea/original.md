```
change_basis!(ret, dest_basis::NodalBasis{Domain},
              values, src_basis::NodalBasis{Domain}) where {Domain<:AbstractDomain}
```

Perform the change of basis for the coefficients `values` from `src_basis` to `dest_basis` and store the resulting coefficients in `ret`.
