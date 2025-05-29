```
(new_trace, weight, retdiff) = regenerate(trace, args::Tuple, argdiffs::Tuple,
                                          selection::Selection)
```

Update a trace by changing the arguments and/or randomly sampling new values for selected random choices using the internal proposal distribution family.

Given a previous trace $(x, r, t)$ (`trace`), new arguments $x'$ (`args`), and a set of addresses $A$ (`selection`), return a new trace $(x', t')$ (`new_trace`) such that $t'$ agrees with $t$ on all addresses not in $A$ ($t$ and $t'$ may have different sets of addresses).  Let $u$ denote the restriction of $t$ to the complement of $A$.  Sample $t' \sim Q(\cdot; u, x')$ and sample $r' \sim Q(\cdot; x', t')$. Return the new trace $(x', r', t')$ (`new_trace`) and the weight (`weight`):

$$
\log \frac{p(r', t'; x')}{q(t'; u, x') q(r'; x', t')}
- \log \frac{p(r, t; x)}{q(t; u', x) q(r; x, t)}
$$

where $u'$ is the restriction of $t'$ to the complement of $A$.

Note that `argdiffs` is expected to be the same length as `args`. If the function that generated `trace` supports default values for trailing arguments, then these arguments can be omitted from `args` and `argdiffs`. Note that if the original `trace` was generated using non-default argument values, then for each optional argument that is omitted, the old value will be over-written by the default argument value in the regenerated trace.
