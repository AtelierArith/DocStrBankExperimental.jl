```
create_nRTRn(cache::BasicILMCache[;scale=1.0])
```

Using the provided cache `cache`, construct the square matrix $n\cdot R_f^T R_f n \circ$, which maps data of type `ScalarData` to data of the same type. The operators `R_f^T` and `R_f` correspond to the interpolation and regularization matrices. The optional keyword `scale` multiplies the matrix by the designated value.
