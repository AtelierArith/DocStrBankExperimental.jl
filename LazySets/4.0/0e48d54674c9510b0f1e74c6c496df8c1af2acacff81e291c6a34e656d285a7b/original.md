σ(d::AbstractVector, msa::MinkowskiSumArray)

Return a support vector of a Minkowski sum of a finite number of sets in a given direction.

### Input

  * `d`   – direction
  * `msa` – Minkowski sum of a finite number of sets

### Output

A support vector in the given direction. If the direction has norm zero, the result depends on the summand sets.
