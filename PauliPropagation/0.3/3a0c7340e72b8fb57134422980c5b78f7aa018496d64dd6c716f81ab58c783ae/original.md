```
filter!(psum::PauliSum, filterfunc::Function)
```

Filter a `PauliSum` in-place by removing all Pauli strings that satisfy the `filterfunc`.
