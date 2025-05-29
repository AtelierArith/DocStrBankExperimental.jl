```
kr_axpy!(A, X, Y)
```

Overwrite `Y` with `A ⊙ X + Y`, where `⊙` stands for the Khatri-Rao (columnwise  Kronecker) product. `A` and `X` need to have same number of columns.
