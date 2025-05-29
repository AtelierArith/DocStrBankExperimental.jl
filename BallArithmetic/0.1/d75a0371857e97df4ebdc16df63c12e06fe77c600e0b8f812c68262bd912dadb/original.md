```
collatz_upper_bound_L2_opnorm(A::BallMatrix; iterates=10)
```

Give a rigorous upper bound on the ℓ² norm of the matrix `A` by using the Collatz theorem.

We use Perron theory here: if for two matrices with `B` positive `|A| < B` we have ρ(A)<=ρ(B) by Wielandt's theorem [Wielandt's theorem](https://mathworld.wolfram.com/WielandtsTheorem.html)

The keyword argument `iterates` is used to establish how many times we are iterating the vector of ones before we use Collatz's estimate.
