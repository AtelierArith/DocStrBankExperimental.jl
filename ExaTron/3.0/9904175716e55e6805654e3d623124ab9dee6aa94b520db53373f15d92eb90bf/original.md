Subroutine dcauchy

This subroutine computes a Cauchy step that satisfies a trust region constraint and a sufficient decrease condition.

Ths Cauchy step is computed for the quadratic

```
q(s) = 0.5*s'*A*s + g'*s
```

where A is a symmetric matrix in compressed row storage, and g is a vector. Given a parameter alpha, the Cauchy step is

```
s[alpha] = P[x - alpha*g] - x,
```

with P the projection onto the n-dimensional interval [xl,xu]. The Cauchy step satisfies the trust region constraint and the sufficient decrease condition

```
|| s || <= delta,    q(s) <= mu_0*(g'*s),
```

where mu_0 is a constant in (0,1).

MINPACK-2 Project. March 1999. Argonne National Laboratory. Chih-Jen Lin and Jorge J. More'.
