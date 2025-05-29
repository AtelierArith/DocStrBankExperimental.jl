```
jacobi_zeros(m, alpha, beta, x)
```

Compute the zeros of Jacobi polynomials

This function computes the zeros of Jacobi polynomials:

  * :P_m

    ^{a,b}(x) = 0 $

The `jacobi_zeros!` is the modifying version and the memory where the zeros will be stored are preallocated. The non-modifying version, `jacobi_zeros` allocates a the memory and calls the modifying version. The function `legendre_zeros` compute the zeros of Legendre polynomials (`a = b = 0`)

Parameters:

  * `m` Order of polynomial
  * `alpha` Weight α of the Jacobi polynomial
  * `beta` Weight β of the Jacobi polynomial
  * `x` Place to store the zeros
  * `T` A float type to compute the zeros
  * returns: the array with zeros.

# Examples

```julia-repl
z = jacobi_zeros(7, 0.3, 0.2)
```
