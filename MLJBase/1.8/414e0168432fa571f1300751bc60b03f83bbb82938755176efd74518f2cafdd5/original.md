```
complement(folds, i)
```

The complement of the `i`th fold of `folds` in the concatenation of all elements of `folds`. Here `folds` is a vector or tuple of integer vectors, typically representing row indices or a vector, matrix or table.

```julia
complement(([1,2], [3,], [4, 5]), 2) # [1 ,2, 4, 5]
```
