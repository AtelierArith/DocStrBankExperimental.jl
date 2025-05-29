Subroutine dprsrch

This subroutine uses a projected search to compute a step that satisfies a sufficient decrease condition for the quadratic

```
q(s) = 0.5*s'*A*s + g'*s,
```

where A is a symmetric matrix in compressed column storage, and g is a vector. Given the parameter alpha, the step is

```
s[alpha] = P[x + alpha*w] - x,
```

where w is the search direction and P the projection onto the n-dimensional interval [xl,xu]. The final step s = s[alpha] satisfies the sufficient decrease condition

```
q(s) <= mu_0*(g'*s),
```

where mu_0 is a constant in (0,1).

The search direction w must be a descent direction for the quadratic q at x such that the quadratic is decreasing in the ray x + alpha*w for 0 <= alpha <= 1.

MINPACK-2 Project. March 1999. Argonne National Laboratory. Chih-Jen Lin and Jorge J. More'.
