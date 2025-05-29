```
construct_hamiltonian([T, ]sys, terms...[; field, auto_pbc_field])
construct_hamiltonian([T, ]lat[, internal, terms...; field, auto_pbc_field])
```

与えられたシステムのためにハミルトニアンを構築します。`construct_operator`と同じことをしますが、結果を`Hamiltonian`型でラップします。
