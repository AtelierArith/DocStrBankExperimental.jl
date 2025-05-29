```
newton_lift(E::EllipticCurve, P::EllipticCurvePoint, reduction_map; max_iterations=7) -> Bool, EllipticCurvePoint
```

Return a point `Q` of `E` which reduces by `reduction_map` to `P` and whether it exists.

Let $F$ be a number field and $E$ an elliptic curve over $F(t)$ which is integral over $F[t]$. Let $O_F$ be the maximal order of $F$ and $p$ be a prime ideal of $O_F$ with residue field $k$. Suppose that $E$ is integral over $(O_F)_p$ and that it has good reduction at $p$.

The algorithm lifts `P` by a multivariate Newton iteration to a point in the completion of $F$ at the prime $p$ (up to some finite precision). The corresponding point of small height in `F` is computed and the result verified.

Throws an error if `max_iterations` is reached without recognizing the point in `F`. Use `set_verbosity_level(:NewtonLift, 2)` for output during the computation.

Input:

  * `E` – the elliptic curve $E/F(t)$
  * `p` – a point of $E/k(t)$
  * `reduction map` – the canonical homomorphism $O_F \rightarrow k$
  * max_iterations – the maximal number of Newton iteration steps, setting to a high value slows down computations a lot.
