```
occsdod(; kwargs...)
occsdod(object, X; kwargs...)
```

One-class classification using a consensus between PCA/PLS score and orthogonal      distances (SD and OD).

  * `fitm` : The preliminary model (e.g. object `fitm` returned by function `pcasvd`) that was fitted on    the training data assumed to represent the training class.
  * `X` : Training X-data (n, p), on which was fitted the model `fitm`.

Keyword arguments:

  * `cut` : Type of cutoff. Possible values are: `:mad`, `:q`. See Thereafter.
  * `cri` : When `cut` = `:mad`, a constant. See thereafter.
  * `risk` : When `cut` = `:q`, a risk-I level. See thereafter.

In this method, the outlierness `d` of a given observation is a consensus between the score distance (SD) and the orthogonal distance (OD). The consensus is computed from the standardized distances by: 

  * `dstand` = sqrt(`dstand_sd` * `dstand_od`).

See functions:

  * `occsd` for details of the outputs,
  * and `occod` for examples.
