```
is_povm_element(M :: AbstractMatrix; atol=ATOL :: Float64) :: Bool
```

Returns `true` if matrix `M` satisfies the following constraints:

  * `M` is Hermitian
  * `M` is positive semi-definite
