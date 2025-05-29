```
computational_basis_vectors( dim::Int64 ) ::Vector{ Vector{Int64} }
```

次の次元 `dim` のベクトル空間を張る直交正規列ベクトルの集合 $\{|1\rangle,\dots,|i\rangle,\dots,|d\rangle \}$ を返します。$|1\rangle = ( 1, 0, \dots, 0 )^T$ であることに注意してください。
