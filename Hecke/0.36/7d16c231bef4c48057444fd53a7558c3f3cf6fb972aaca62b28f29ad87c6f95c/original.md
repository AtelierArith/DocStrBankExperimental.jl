```
  is_subfield_normal(K::AbsSimpleNumField, L::AbsSimpleNumField) -> Bool, NumFieldHom{AbsSimpleNumField, AbsSimpleNumField}
```

Returns `true` and an injection from $K$ to $L$ if $K$ is a subfield of $L$. Otherwise the function returns `false` and a morphism mapping everything to `0`.

This function assumes that $K$ is normal.
