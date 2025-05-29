Slice sampler based on [Neal, 2003](https://projecteuclid.org/journals/annals-of-statistics/volume-31/issue-3/Slice-sampling/10.1214/aos/1056562461.full).

Fields:

  * `w`:  Initial slice size.
  * `p`:  Slices are no larger than 2^p * w
  * `n_passes`:  Number of passes through all variables per exploration step.
  * `max_iter`:  Maximum number of interations inside shrink_slice! before erroring out
