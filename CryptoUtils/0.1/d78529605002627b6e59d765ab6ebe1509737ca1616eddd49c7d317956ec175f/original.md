```
is_quadratic_residue(a::Integer, p::Integer) -> Bool
```

Return true or false depending on wheter `a` is a quadratic residue mod `p`.

That is, it checks if `x^2 == a mod p` has solutions.
