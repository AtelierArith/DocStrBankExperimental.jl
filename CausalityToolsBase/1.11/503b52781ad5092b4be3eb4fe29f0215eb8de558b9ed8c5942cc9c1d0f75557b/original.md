```
Positions
```

Wrapper type for the positions the different dynamical variables appear in when  constructing a custom state space reconstruction. Used in combination with `Lags` to specify how a `CustomReconstruction` should be constructed. Each  of the positions must refer to a dynamical variable (column) actually present in the  dataset.

## Examples

  * `Positions(1, 2, 1, 5)` indicates a 4-dimensional state space reconstruction where 

    1. the 1st coordinate axis of the reconstruction should be formed from the

    first variable/column of the input data.

    2. the 2nd coordinate axis of the reconstruction should be formed from the

    2nd variable/column of the input data.

    3. the 3rd coordinate axis of the reconstruction should be formed from the

    1st variable/column of the input data.

    4. the 4th coordinate axis of the reconstruction should be formed from the

    5th variable/column of the input data.
  * `Positions(-1, 2)` indicates a 2-dimensional reconstruction, but will not work, because    each position must refer to the index of a dynamical variable (column) of a dataset    (indexed from 1 and up).
