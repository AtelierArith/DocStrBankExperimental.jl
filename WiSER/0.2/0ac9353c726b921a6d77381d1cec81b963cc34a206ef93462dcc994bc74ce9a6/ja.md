```
kron_axpy!(A, X, Y)
```

`Y`を`A ⊗ X + Y`で上書きします。`Y += kron(A, X)`と同じですが、よりメモリ効率が良いです。
