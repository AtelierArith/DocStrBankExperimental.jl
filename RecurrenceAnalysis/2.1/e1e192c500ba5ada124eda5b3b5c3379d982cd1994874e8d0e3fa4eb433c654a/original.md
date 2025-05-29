```
determinism(R[; lmin=2, theiler])
```

Calculate the determinism of the recurrence matrix `R`:

## Description

The determinism is calculated as:

$$
DET = \frac{\sum_{l=lmin}{l P(l)}}{\sum_{l=1}{l P(l)}} =
\frac{\sum_{l=lmin}{l P(l)}}{\sum R}
$$

where $l$ stands for the lengths of diagonal lines in the matrix, and $P(l)$ is the number of lines of length equal to $l$.

`lmin` is set to 2 by default, and this calculation rules out all the points inside the Theiler window (see [`rqa`](@ref) for the default values and usage of the keyword argument `theiler`).
