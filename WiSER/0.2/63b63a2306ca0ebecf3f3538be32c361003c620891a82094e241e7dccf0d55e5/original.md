```
mul!(result, Ct::Transpose{Int, CopyMatrix}, A)
```

Left-multiplying a matrix `A` by transpose of a copying matrix is equivalent to  keeping the rows of `A` corresponding to the lower triangular indices.
