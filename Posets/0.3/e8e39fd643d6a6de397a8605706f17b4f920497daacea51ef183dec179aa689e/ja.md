```
strict_zeta_matrix(p::Poset)
```

`p`の*厳密*ゼータ行列を返します。これは、`i,j`のエントリが`p[i] < p[j]`のときに正確に`1`である（密な）0,1行列です。`zeta_matrix`も参照してください。
