```
uniform(r = 1.0)
```

Returns an in-place real valued mutation function that performs the uniform distributed mutation [^1].

The mutation operator randomly chooses a number $z$ in from the uniform distribution on the interval $[-r,r]$, the mutation range. The mutated individual is given by

  * $x_i^\prime = x_i + z_i$
