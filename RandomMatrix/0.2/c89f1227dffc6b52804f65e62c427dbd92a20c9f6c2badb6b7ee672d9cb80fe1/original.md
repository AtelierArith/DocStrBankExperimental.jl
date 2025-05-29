```julia
Haar(beta,n)
```

  * Uniform distribution on O(n) (`beta = 1`), U(n) (`beta = 2`)
  * `beta`: 1 for Orthogonal, 2 for Unitary
  * `n`: dimension

```julia
# Examples

# Generate a 100 by 100 random Unitary Matrix uniformly from U(n)
rand(Haar(2,100))


# Generate a 100 by 100 random Orthogonal Matrix uniformly from O(n)
rand(Haar(1,100))
```
