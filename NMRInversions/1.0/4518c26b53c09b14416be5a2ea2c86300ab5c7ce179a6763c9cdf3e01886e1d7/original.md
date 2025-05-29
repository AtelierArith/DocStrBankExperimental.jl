```
svd_kernel_struct(K,g,U,S,V)
```

A structure containing the following fields:

  * `K`, the kernel matrix.
  * `G`, the data vector.
  * `U`, the left singular values matrix.
  * `S`, the singular values vector.
  * `V`, the right singular values matrix.

To access the fields of a structure, we use the dot notation,  e.g. if the structure is called `a` and we want to access the kernel contained in there, we type `a.K`
