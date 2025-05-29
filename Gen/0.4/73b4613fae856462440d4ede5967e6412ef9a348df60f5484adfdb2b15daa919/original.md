```
(weight, retval) = assess(gen_fn::GenerativeFunction, args::Tuple, choices::ChoiceMap)
```

Return the probability of proposing an assignment

Given arguments $x$ (`args`) and an assignment $t$ (`choices`) such that $p(t; x) > 0$, sample $r \sim q(\cdot; x, t)$ and return the weight (`weight`):

$$
\log \frac{p(r, t; x)}{q(r; x, t)}
$$

It is an error if $p(t; x) = 0$.
