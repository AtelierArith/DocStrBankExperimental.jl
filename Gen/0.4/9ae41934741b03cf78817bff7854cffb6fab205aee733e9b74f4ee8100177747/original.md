```
weight = project(trace::U, selection::Selection)
```

Estimate the probability that the selected choices take the values they do in a trace.

Given a trace $(x, r, t)$ (`trace`) and a set of addresses $A$ (`selection`), let $u$ denote the restriction of $t$ to $A$. Return the weight (`weight`):

$$
\log \frac{p(r, t; x)}{q(t; u, x) q(r; x, t)}
$$
