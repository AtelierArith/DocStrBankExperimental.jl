```
sparsity(sym_func::AbstractArray{<:Node})
```

Computes a number representing the sparsity of the array of expressions. If `nelts` is the number of elements in the array and `nzeros` is the number of zero elements in the array then `sparsity = (nelts-nzeros)/nelts`. 

Frequently used in combination with a call to `make_function` to determine whether to set keyword argument `init_with_zeros` to false.
