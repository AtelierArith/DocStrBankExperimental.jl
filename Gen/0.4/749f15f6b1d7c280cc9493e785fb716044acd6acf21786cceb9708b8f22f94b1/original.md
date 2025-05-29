```
(choices, weight, retval) = propose(gen_fn::GenerativeFunction, args::Tuple)
```

Sample an assignment and compute the probability of proposing that assignment.

Given arguments (`args`), sample $t \sim p(\cdot; x)$ and $r \sim p(\cdot; x, t)$, and return $t$ (`choices`) and the weight (`weight`):

$$
\log \frac{p(r, t; x)}{q(r; x, t)}
$$
