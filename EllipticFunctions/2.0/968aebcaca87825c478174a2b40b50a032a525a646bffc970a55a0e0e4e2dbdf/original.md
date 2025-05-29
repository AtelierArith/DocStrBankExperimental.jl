```
jellip(kind, u; tau, m)
```

Jacobi elliptic functions. Only one of the parameters `tau` or `m` must be supplied.

# Arguments

  * `kind`: a string with two characters among 'c', 'd', 'n' or 's'; this string specifies the function: the two letters respectively denote the basic functions `sn`, `cn`, `dn` and `1`, and the string specifies the ratio of two such functions, e.g. `ns=1/sn` and `cd=cn/dn`
  * `u`: a real or complex number or array of numbers
  * `tau`: complex number with nonnegative imaginary part
  * `m`: real or complex number, square of the elliptic modulus
