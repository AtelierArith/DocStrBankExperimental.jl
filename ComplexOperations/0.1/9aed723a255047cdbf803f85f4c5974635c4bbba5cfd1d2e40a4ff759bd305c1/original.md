```
Calculate the inverse of a complex matrix A+iB, where A and B are real matrices
```

There are two possible versions: Version #1: This one preallocate. Faster and use more memory for 1M evaluations: 1.771474 seconds (14.18 M allocations: 4.510 GiB, 4.52% gc time, 6.40% compilation time) `function complex_matrix_inversion(A, B)     inv_A_B = inv(A) * B     C = inv(A + B * inv_A_B)     D = -inv_A_B * C     return C, D end`

Version #2: No preallocation. Slower and use less memory for 1M evaluations: 2.330454 seconds (19.00 M allocations: 6.512 GiB, 2.71% gc time) `function complex_matrix_inversion(A, B)         C = inv(A + B * inv(A) * B)     D = -1 .* inv(A) * B * C     return C, D end`
