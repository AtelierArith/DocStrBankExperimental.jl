Crossing minimization by sorting a univariate statistic.

The boxes in `sources` and/or `targets` are fixed and the boxes in `vs` are permuted. A permutation `σ` of the latter is returned, such that `vs[σ]` are the sorted box IDs. Both one-sided and two-sided crossing minimization are supported, depending on whether just one, or both, of `sources` and `targets` are given.

In this simple but popular heuristic algorithm, the boxes are permuted by sorting a univariate statistic of the positions of incoming and/or outgoing wires. Typical choices are:

  * `mean`: the sample mean, yielding the "barycenter method"
  * `median`: the sample median

In both cases, this algorithm has the property that if there is a permutation with no crossings, it will find it.
