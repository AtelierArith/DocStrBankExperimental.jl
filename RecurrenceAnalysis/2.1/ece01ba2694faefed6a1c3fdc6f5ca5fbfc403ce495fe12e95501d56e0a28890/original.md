```
laminarity(R[; lmin=2, theiler])
```

Calculate the laminarity of the recurrence matrix `R`.

## Description

The laminarity is calculated as:

$$
LAM = \frac{\sum_{v=lmin}{v P(l)}}{\sum_{v=1}{v P(v)}} =
\frac{\sum_{v=lmin}{v P(l)}}{\sum R}
$$

where $v$ stands for the lengths of vertical lines in the matrix, and $P(v)$ is the number of lines of length equal to $v$.

`lmin` is set to 2 by default, and this calculation rules out all the points inside the Theiler window (see [`rqa`](@ref) for the default values and usage of the keyword argument `theiler`).
