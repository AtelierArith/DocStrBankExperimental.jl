```
(new_trace, weight, retdiff, discard) = update(trace, args::Tuple, argdiffs::Tuple,
                                               constraints::ChoiceMap)
```

Update a trace by changing the arguments and/or providing new values for some existing random choice(s) and values for some newly introduced random choice(s).

Given a previous trace $(x, r, t)$ (`trace`), new arguments $x'$ (`args`), and a map $u$ (`constraints`), return a new trace $(x', r', t')$ (`new_trace`) that is consistent with $u$.  The values of choices in $t'$ are either copied from $t$ or from $u$ (with $u$ taking precedence) or are sampled from the internal proposal distribution.  All choices in $u$ must appear in $t'$.  Also return an assignment $v$ (`discard`) containing the choices in $t$ that were overwritten by values from $u$, and any choices in $t$ whose address does not appear in $t'$. Sample $t' \sim q(\cdot; x', t + u)$, and $r' \sim q(\cdot; x', t')$, where $t + u$ is the choice map obtained by merging $t$ and $u$ with $u$ taking precedence for overlapping addresses.  Also return a weight (`weight`):

$$
\log \frac{p(r', t'; x')}{q(r'; x', t') q(t'; x', t + u)}
- \log \frac{p(r, t; x)}{q(r; x, t)}
$$

Note that `argdiffs` is expected to be the same length as `args`. If the function that generated `trace` supports default values for trailing arguments, then these arguments can be omitted from `args` and `argdiffs`. Note that if the original `trace` was generated using non-default argument values, then for each optional argument that is omitted, the old value will be over-written by the default argument value in the updated trace.
