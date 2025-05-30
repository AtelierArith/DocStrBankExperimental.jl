```
gamma_inc_taylor_x(a,x,ind)
```

Computes $P(a,x)$ based on Taylor expansion of $P(a,x)/x^a$ given by:

$$
J = -a * \sum_{1}^{\infty} (-x)^{n}/((a+n)n!)
$$

and $P(a,x)/x^a$ is given by:

$$
(1 - J) / \Gamma(a+1)
$$

resulting from term-by-term integration of `gamma_inc(a,x,ind)`. This is used when `a < 1` and `x < 1.1` - Refer Eqn (9) in the [paper by DiDonato & Morris (1986)](@cite didonato_1986).

See also: [`gamma_inc(a,x,ind)`](@ref SpecialFunctions.gamma_inc)
