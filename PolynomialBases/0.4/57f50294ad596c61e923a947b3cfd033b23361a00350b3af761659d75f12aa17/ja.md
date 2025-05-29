```
function change_basis(dest_basis::NodalBasis{Domain},
                      values, src_basis::NodalBasis{Domain}) where {Domain<:AbstractDomain}
```

係数 `values` の基底を `src_basis` から `dest_basis` に変更します。
