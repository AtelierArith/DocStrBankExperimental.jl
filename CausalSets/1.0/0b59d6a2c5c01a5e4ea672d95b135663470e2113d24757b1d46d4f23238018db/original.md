```
ConformallyTimesliceableManifold{N} <: AbstractManifold{M}
```

Supertype for `N`-dimensional conformally timesliceable manifolds, defined as manifolds whose metric can be brought into the form

$$
\begin{aligned}
\mathrm{d}s^2 = F \left( -\mathrm{d}t^2 + \mathrm{d}X^2 \right)
\end{aligned}
$$

where $F$ is the conformal factor, and $\mathrm{d} X^2$ is some $N-1$-dimensional spatial line element.
