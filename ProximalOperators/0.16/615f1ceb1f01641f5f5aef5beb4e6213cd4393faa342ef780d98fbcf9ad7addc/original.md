```
IndBox(low, up)
```

Return the indicator function of the box

$$
S = \{ x : low \leq x \leq up \}.
$$

Parameters `low` and `up` can be either scalars or arrays of the same dimension as the space: they must satisfy `low <= up`, and are allowed to take values `-Inf` and `+Inf` to indicate unbounded coordinates.
