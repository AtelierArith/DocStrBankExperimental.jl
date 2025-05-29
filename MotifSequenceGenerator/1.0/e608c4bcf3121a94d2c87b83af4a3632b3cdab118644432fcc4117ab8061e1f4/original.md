```
random_sequence(motifs::Vector{M}, q, limits, translate, δq = 0; kwargs...)
```

Create a random sequence of motifs of type `M`, under the constraint that the sequence has "length" `ℓ` **exactly** within `q - δq ≤ ℓ ≤ q + δq`. Return the sequence itself as well as the sequence of indices of `motifs` used to create it. A vector of probabilities `weights` can be given as a keyword argument, which then dictates the sampling probability for each entry of `motifs` for the initial sequence created.

"length" here means an abstracted length defined by the struct `M`, based on the `limits` and `translate` functions. It does **not** refer to the amount of elements!

`M` can be anything, given the two functions

  * `limits(motif)` : Some function that given the `motif` it returns the `(start, fine)` of the the motif in the same units as `q`. This function establishes a measure of length, which simply is `fine - start`.
  * `translate(motif, t)` : Some function that given the `motif` it returns a *new* motif which is translated by `t` (either negative or positive), with respect to the same units as `q`.

## Other Keywords

Please see the source code (use `@which`) for a full description of the algorithm.

  * `tries = 5` : Up to how many initial random sequences are accepted.
  * `taulcut = 2` : Up to how times an element is dropped from the initial guess.
  * `summands = 3` : Up to how many motifs may be combined as a sum to complete a sequence.
