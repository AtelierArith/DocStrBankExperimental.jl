```
GF(p::T; check::Bool=true) where T <: Integer
```

Return the finite field $\mathbb{F}_p$, where $p$ is a prime. By default, the integer $p$ is checked with a probabilistic algorithm for primality. When `check == false`, no check is made, but the behaviour of the resulting object is undefined if $p$ is composite.
